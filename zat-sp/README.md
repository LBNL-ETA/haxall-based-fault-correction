<!-- Output copied to clipboard! -->

<!-----

You have some errors, warnings, or alerts. If you are using reckless mode, turn it off to see inline alerts.
* ERRORs: 0
* WARNINGs: 0
* ALERTS: 10

Conversion time: 3.681 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Fri Jun 02 2023 11:03:28 GMT-0700 (PDT)
* Source doc: Zone temperature setpoint correction - Temperature Setpoints App Notes
* This document has images: check for >>>>>  gd2md-html alert:  inline image link in generated source and store images to your server. NOTE: Images in exported zip file from Google Docs may not appear in  the same order as they do in your doc. Please check the images!

----->


<p style="color: red; font-weight: bold">>>>>>  gd2md-html alert:  ERRORs: 0; WARNINGs: 0; ALERTS: 10.</p>
<ul style="color: red; font-weight: bold"><li>See top comment block for details on ERRORs and WARNINGs. <li>In the converted Markdown or HTML, search for inline alerts that start with >>>>>  gd2md-html alert:  for specific instances that need correction.</ul>

<p style="color: red; font-weight: bold">Links to alert messages:</p><a href="#gdcalert1">alert1</a>
<a href="#gdcalert2">alert2</a>
<a href="#gdcalert3">alert3</a>
<a href="#gdcalert4">alert4</a>
<a href="#gdcalert5">alert5</a>
<a href="#gdcalert6">alert6</a>
<a href="#gdcalert7">alert7</a>
<a href="#gdcalert8">alert8</a>
<a href="#gdcalert9">alert9</a>
<a href="#gdcalert10">alert10</a>

<p style="color: red; font-weight: bold">>>>>> PLEASE check and correct alert issues and delete this message and the inline alerts.<hr></p>



## Introduction

The Temperature Setpoints view displays all supply terminal units for a selected site, along with their related generalized zone temperature setpoints - both current values and reference values.

[These generalized values exclude occupant adjustments and demand controls](https://docs.google.com/document/d/1IDIcmwEAHroG4tCAEJE1OfhH8yeiP3bLEiG2eRmfIj4/edit#heading=h.q8o5us9gnu58), they are:



* Occupied Heating Setpoint
* Occupied Cooling Setpoint
* Unoccupied Heating Setpoint
* Unoccupied Cooling Setpoint

These points have fixed values over long periods of time, and they do not reflect occupant adjustments at the thermostats.



<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")



## Screenshot of Temperature Setpoints view for B91 - only one supply terminal unit is configured in this project

The Temperature Setpoints view highlights in red the current setpoints if they deviate from the reference. It highlights in green the current setpoints that match the reference, and the entire row if all setpoints match their references.

The view also offers two actions, which both require that one row be selected.



* Edit Reference Temperatures: opens a form to edit the reference values
* Push Reference Temperatures: for each input that deviates from its reference, writes reference values to the BMS


## Reference Values

Reference values are stored in folio records, one per terminal unit. The associated template is “referenceZoneTemps”.



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")



## Sample referenceZoneTemps record for B91 SVAV-110



<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.png "image_tooltip")



## Template for referenceZoneTemps


## Current Values

The Temperature Setpoints view is based on the viSiteZoneTempReferenceSetpoints function, which builds a table by cycling through all supply airTerminalUnit equipment records for a selected site, and retrieves current and reference values for each via the viZoneTempSetpoints function. Formatting is then applied, for example to highlight matches and discrepancies.

Function viZoneTempSetpoints loads reference values from folio based on the id of the supply airTerminalUnit, and also queries the supply airTerminalUnit equipment to determine what function to call to obtain the current generalized temperature values. The function name is stored as text in the generalizedSpReadFunc tag.



<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image4.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image4.png "image_tooltip")



## Sample supply airTerminalUnit equip, with generalizedSpReadFunc

Functions that can be used as generalizedSpReadFunc must meet the following requirements:



* First input must be id of supply airTerminalUnit (**equipRef**)
* Output dictionary {**curOccHtg**, **curOccClg**, **curUnoccHtg**, **curUnoccClg**}

The output dictionary must use the specified keys for the current values of generalized inputs:



* **curOccHtg** - Current Occupied Heating Setpoint
* **curOccClg** - Current Occupied Cooling Setpoint
* **curUnoccHtg** - Current Unoccupied Heating Setpoint
* **curUnoccClg** - Current Unoccupied Cooling Setpoint



<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image5.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image5.png "image_tooltip")



## Sample generalizedSpReadFunc for ALC - no conversion needed


## Correction Values

Similarly to current values, the action function recPushReferenceZoneTemps will look up what function to call to correct inputs by writing to the BMS. The function name is stored as text in the generalizedSpWriteFunc tag of the selected supply airTerminalUnit equip.

Functions that can be used as generalizedSpWriteFunc must meet the following requirements:



* Inputs must be, in order (**equipRef**, **occHtgSp**:null, **occClgSp**:null, **unoccHtgSp**:null, **unoccClgSp**:null)
* Input values of null are used for generalized inputs that do not need correction
* Output is optional and will not be used

The dedicated functions are tasked with



* Translating from desired generalized input values to controller input values,
* Writing those values to the controller inputs.



<p id="gdcalert6" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image6.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert7">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image6.png "image_tooltip")



## Sample generalizedSpWriteFunc for ALC - no conversion needed


## Setup Notes

Copy view

Copy template

Copy functions

Set generalizedSpReadFunc and generalizedSpWriteFunc tags on existing supply terminal units



<p id="gdcalert7" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image7.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert8">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image7.png "image_tooltip")



## Modifying existing supply airTerminalUnit records to add generalizedSpReadFunc

Inputs already configured as writable at B91

Set reference temperatures, using the view



<p id="gdcalert8" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image8.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert9">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image8.png "image_tooltip")



## Using the Edit Reference Temperatures button to set the reference temperatures for a zone

Push reference temperatures to the BMS, using the view



<p id="gdcalert9" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image9.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert10">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image9.png "image_tooltip")



## Trends in ALC show changes in setpoint around 11:15, reversed manually after a few minutes

This generates a fairly long audit log note in ALC



<p id="gdcalert10" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image10.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert11">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image10.png "image_tooltip")



## Audit log in ALC after zone temperature setpoint correction