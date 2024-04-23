---
name: Testing checklist template
about: Use this template to create an issue for regression testing
---

## 1 - Transfer Types

### 1.1

**Severity**: Medium

Given the user is processing a Transfer but they want to use decision point settings that are different from the “Default” processing configuration.

When they have defined additional processing configuration profiles in in the Archivematica Administration tab (e.g. “mycustom_processing_config”)
- [ ] Then the user can select this processing configuration as a dropdown option next to the "Start Transfer" button.
- [ ] The user will receive a pop-up notification indicating that the Transfer has started with the selected processing configuration (e.g. “mycustom_processing_config”).
- [ ] The Transfer and Ingest processing will follow the decisions set out in the newly selected processing configuration file rather than the “default” processing configuration.
- [ ] The next time the user presses the “Start Transfer” button, but does not select a processing configuration option, they will receive a pop-up notification that the Transfer has started with the “default” processing configuration and the Transfer and Ingest processing will follow the “default” processing configuration settings.

### 1.2

When *SampleTransfer/ZippedDirectoryTransfers/DemoTransferCSV.zip* is processed using the Zipped Directory transfer type
- [ ] The Extract zipped bag transfer job executes successfully
- [ ] All microservices execute successfully
- [ ] All standard AIP structure and METS structure criteria apply

### 1.3

**Severity**: High

**External tools**: 7zip

When *SampleTransfer/ZippedBag.zip* is processed using the Zipped Bag transfer type
- [ ] The Bag Verification microservice executes successfully AND
- [ ] All standard AIP structure and METS structure criteria apply AND
- [ ] The contents of bag-info.txt (if any) are parsed into METS

### 1.4

**Severity**: High

When *SampleTransfer/DSpaceExport* (or one of the zips contained inside) is processed using the DSpace transfer type
- [ ] The Identify DSpace files microservice executes successfully AND
- [ ] All standard AIP structure and METS structure criteria apply

### 1.5

**Severity**: Medium

**External tools**: tsk_recover (Sleuthkit), unrar-free

When *SampleTransfer/ISODiskImage* is processed using the Disk Image transfer type AND disk image metadata has been added before the transfer is started
- [ ] The disk image metadata ends up in the AIP METS AND
- [ ] All standard AIP structure and METS structure criteria apply

## 2 - Transfer Variants

### 2.1

**Severity**: High

**Current coverage in AMAUAT**: Ok / Implicit

**AMAUAT tests**: create-aip.feature

When a transfer containing descriptive and rights metadata (*SampleTransfer/DemoTransferCSV*) is processed
- [ ] The AIP METS contains descriptive metadata for each of the objects described in the metadata.csv AND
- [ ] The AIP METS contains rights metadata for each of the objects described in the rights.csv

### 2.2

**Severity**: High

**Current coverage in AMAUAT**: Ok / Implicit

When a Transfer containing Submission Documentation (*SampleTransfer/DemoTransferCSV*) is processed
- [ ] Submission documentation is listed in the METS with fileGrp USE="submissionDocumentation"

### 2.3

**Severity**: Medium

When a transfer containing multi-level descriptive metadata (*SampleTransfer/CSVmultiLevel*) is processed
- [ ] The AIP METS contains descriptive metadata for each of the directories described in the metadata.csv

### 2.4

**Severity**: High

**Current coverage in AMAUAT**: Ok / Implicit

When a transfer containing descriptive metadata for individual files using a metadata.csv (*SampleTransfer/CSVmetadata*) is processed
- [ ] The AIP METS contains descriptive metadata for each of the files described in the metadata.csv

### 2.5

**Severity**: High

When a transfer with files that have been manually normalized outside of Archivematica (*TestTransfers/ManualNormalization*) is processed, and "Normalize for preservation and access" is selected at the Normalization microservice
- [ ] Originals should be .dat, .TGA, and .GIF AND
- [ ] Preservation copies should be .prk and .tif (there is no preservation copy made of the GIF) AND
- [ ] Access copies should be .bmp, .jpg, and .jpg.

### 2.6

**Severity**: High

With “Normalization” set to None and “Approve normalization” set to None in the default processing config, process a transfer using *SampleTransfers/AccessCopies*, “Job: Normalize” should only give three options - choose “Normalize for preservation”.
- [ ] Originals should be .png AND
- [ ] No preservation copies should be generated (PNG is already considered a preservation format) AND 
- [ ] Access copies should be .gif

### 2.7

**Severity**: Medium

With “Normalization” set to None and “Approve normalization” set to None in the default processing config, run SampleTransfers/ServiceCopies transfer and choose “Normalize service files for access”.
- [ ] "Job Normalize service files for access" should run AND 
- [ ] the task output should show that the service files were used to create access copies.

### 2.8

**Severity**: Medium

When *SampleTransfers/ProcessingMCP* is processed using the Standard transfer type
- [ ] then the Transfer and Ingest processing will follow the decisions set out in the processing configuration XML file, rather than the default configuration

### 2.9

**Severity**: Medium

When *SampleTransfers/BagExamples/SimpleBagWithProcessingMCP* is processed as a Zipped Bag transfer
- [ ] then the Transfer and Ingest processing will follow the decisions set out in the processing configuration XML file, rather than the default configuration

### 2.10

Given that a transfer contains a premis.xml file (*SampleTransfers/PremisImporter*)

When the premis.xml file is parsed into the Archivematica METS file
- [ ] Then the PREMIS XML import file's Event and Agent entities are added to the Archivematica AIP METS file AND
- [ ] the Events retain their original field values, including the event details AND
- [ ] the Events are linked to the same Agents as in the PREMIS XML import file

### 2.11

Given that a transfer contains an identifiers.json file (*SampleTransfers/DemoTransferCSV*)

When the identifiers.json file is imported into Archivematica after the Objects are ingested
- [ ] Then the identifiers from the JSON file are mapped as objectIdentifiers in the METS file

## 3 - Virus scanning

### 3.1

**Severity**: High

**AMAUAT tests**: virus.feature

When a transfer containing a virus is processed (*TestTransfers/virusTests*)
- [ ] The job "Scan for viruses" will fail AND
- [ ] The standard streams will report which files failed virus scanning

## 4 - Special Characters

### 4.1

**Severity**: High

When a transfer contains files and directories with non-ASCII characters in the file/directory name (*TestTransfers/badNames*)
- [ ] Then the "Change transfer filenames" microservice will complete successfully AND
- [ ] the AIP will contain a name cleanup log AND
- [ ] a name cleanup PREMIS event will be present in the METS

### 4.2

**Severity**: Medium

When the transfer name contains non-ASCII characters
- [ ] Then the "Change transfer filenames" microservice will complete successfully AND
- [ ] the transfer’s name will be changed to use ASCII characters

### 4.3

When a transfer contains files with non-ASCII characters in the file name as well as a metadata.csv file (*SampleTransfers/DiacriticsTest*)
- [ ] Then the "Change transfer filenames" microservice will complete successfully AND
- [ ] the AIP will contain a name cleanup log AND 
- [ ] a name cleanup PREMIS event will be present in the METS AND
- [ ] the METS will contain descriptive metadata for each of the files described in the metadata.csv

## 5 - File Identification

### 5.1

**Severity**: High

**External tools**: Siegfried

Given that Siegfried is set as the file identification tool

AND the Processing Configuration in the Administration settings has "Perform file format identification (Transfer)" set to Yes

When a transfer that includes known formats is processed (e.g. *SampleTransfers/Images*)
- [ ] Then Siegfried successfully identifies the formats during the *Identify File Format* microservice

### 5.2

**Severity**: High

**External tools**: Siegfried

Given that Siegfried is set as the file identification tool

When a transfer includes a format that is unknown to Siegfried (try sampleTransfers/Multimedia) and is processed with "Perform file format identification (Transfer)" set to Yes
- [ ] Then Job: Identify file format shows as failed in the dashboard AND
- [ ] The stderr shows which file cannot be identified AND
- [ ] The premis:formatName field for the premis Object has a value of unknown AND
- [ ] There is no format identification Event for the file

### 5.3

**Severity**: High

**External tools**: Fido

Given that Fido is set as the file identification tool

When a transfer is processed with "Perform file format identification (Transfer)" set to Yes
- [ ] Then Fido is able to identify file formats and versions accurately AND
- [ ] one <premis:eventType>format identification</premis:eventType> for each file will be present in the METS
- [ ] the premis:eventDetail will indicate that Fido was the tool used

### 5.4

**Severity**: High

**External tools**: Fido

Given that Fido is set as the file identification tool

AND the Processing Configuration in the Administration settings has "Perform file format identification (Transfer)" set to Yes

When a transfer that includes known formats is processed (e.g. *SampleTransfers/Images*)
- [ ] Then Fido successfully identifies the formats during the *Identify File Format* microservice

### 5.5

**Severity**: High

**External tools**: Fido

Given that Fido is set as the file identification tool

When a transfer includes a format that is unknown to Fido is processed with "Perform file format identification (Transfer)" set to Yes
- [ ] Then Job: Identify file format shows as failed in the dashboard AND
- [ ] The stderr shows which file cannot be identified AND
- [ ] The premis:formatName field for the premis Object has a value of unknown AND
- [ ] There is no format identification Event for the file

### 5.6

**Severity**: High

**External tools**: File extension script

Given that File Extension is set as the file identification tool

When a transfer is processed with "Perform file format identification (Transfer)" set to Yes
- [ ] Then the format should be identified based on its file extension AND
- [ ] a format identification PREMIS event is created AND
- [ ] the premis:eventDetail indicates that File Extension version="0.1" was the tool used

### 5.7

**Severity**: Medium

When a transfer is processed with "Perform file format identification (Transfer)" set to No
- [ ] Then the standard output for the job "Identify file format" will be "Skipping file format identification" AND
- [ ] there will be no format identification PREMIS events for the transfer objects in the METS

## 6 - Package Extraction

### 6.1

**Severity**: Medium

When a transfer containing a package (*SampleTransfers/OfficeDocs*) is processed with "Extract packages" set to Yes and "Delete packages after extraction" set to Yes
- [ ] The resulting AIP will not contain the original package

### 6.2

**Severity**: Medium

When a transfer containing a package (*SampleTransfers/OfficeDocs*) is processed with "Extract packages" set to Yes and "Delete packages after extraction" set to No
- [ ] The resulting AIP will contain the original package

## 7 - Characterization

### 7.1

**Severity**: High

**Current coverage in AMAUAT**: TBC - need to check which tools we use now

**External tools**: FFprobe, ExifTool, MediaInfo, FITS, fiwalk (Sleuthkit)

When a transfer is processed
- [ ] Then the "Characterize and extract metadata" microservice will run AND
- [ ] the appropriate characterization tool for a given format will be triggered AND
- [ ] the characterization tool outputs will be captured in the premis:objectCharacteristicsExtension container

## 8 - Validation

### 8.1

**Severity**: Medium

**Current coverage in AMAUAT**: TBC

**External tools**: MediaConch

When a transfer containing Matroska files (*SampleTransfers/Matroska*) is processed
- [ ] Then the job "Validate formats" will complete successfully AND
- [ ] it will contain accurate validation information for the Matroska files AND
- [ ] one <premis:eventType>validation</premis:eventType> for each file will be present in the METS AND
- [ ] the premis:eventDetail for the validation event will indicate that MediaConch was the tool used

## 9 - Normalization

### 9.1

**Severity**: High

Given that a transfer contains file formats for which there are preservation and access normalization rules
When the user selects "normalize for preservation and access" at the Normalize job
- [ ] Then the files will be normalized for preservation and access as per the rules AND
- [ ] the preservation derivatives will be added to the AIP with a UUID suffix and the appropriate file extension AND
- [ ] the access derivatives will be added to the DIP AND
- [ ] normalization premis events will be added to the METS

### 9.2

**Severity**: Medium

**External tools**: convert (ImageMagick)

When a transfer is processed with "Generate thumbnails" set to Yes
- [ ] Then thumbnails will be created for all digital objects in the AIP

### 9.3

**Severity**: High

Given that a transfer contains file formats for which there are preservation normalization rules

When the user selects "normalize for preservation" at the Normalize job
- [ ] Then the files will be normalized for preservation as per the rules AND
- [ ] the preservation derivatives will be added to the AIP with a UUID suffix and the appropriate file extension AND
- [ ] normalization premis events will be added to the METS

### 9.4

**Severity**: Medium

Given that a transfer contains service files (*SampleTransfers/ServiceCopies*)

When the user selects "normalize service files for access" at the Normalize job
- [ ] Then the service files be used to create the access derivatives AND
- [ ] the access derivatives will be added to the DIP

### 9.5

**Severity**: High

Given that a transfer contains file formats for which there are normalization rules

When the user selects "do not normalize" at the Normalize job
- [ ] Then normalization will not occur AND
- [ ] the AIP will contain originals only

### 9.6

**Severity**: Medium

Given that a user selects "normalize manually" at the Normalize job

When the user manually inserts normalized files into the SIP (by accessing the pipeline's processing location directly via SSH or SFTP) using the required directory structure (see documentation)

And then selects "Approve" at the Approve normalization job
- [ ] The "Process manually normalized files" will be completed successfully AND
- [ ] the preservation derivatives will be added to the AIP with a UUID suffix and the appropriate file extension AND
- [ ] the access derivatives will be added to the DIP

### 9.7

**Severity**: Medium

Given that the user has manually normalized the files as per 9.1.5

When the user clicks on the metadata icon and then "Manual normalization event detail"
- [ ] Then the user will be able to enter normalization event information for the manual normalization action AND
- [ ] the event information will be added to the METS

### 9.8

**Severity**: High

Given that a transfer contains file formats for which there are access normalization rules

When the user selects "normalize for access" at the Normalize job
- [ ] Then access derivatives will be created and added to the DIP AND
- [ ] the AIP will contain originals only

### 9.9

**Severity**: Medium

Given that a transfer includes an access directory with manually normalized access derivatives (*SampleTransfers/AccessCopies*)

When the user reaches the Normalize job
- [ ] Then the dropdown will only have two normalization options ("Normalize for preservation" and "Do not normalize") AND
- [ ] regardless of the option picked, a DIP will be created with the access copies from the transfer

### 9.10

**Severity**: Medium

Given that a transfer includes a preservation directory with manually normalized preservation derivatives (*SampleTransfers/PreservationCopies*)

When the user reaches the Normalize job and chooses "Normalize for Preservation"
- [ ] Then normalization will not occur during the Normalization microservice AND
- [ ] the "Process manually normalized files" microservice will recognize the manualNormalization/preservation directory AND
- [ ] UUIDs will be assigned to the preservation copies and included in their filenames AND
- [ ] the AIP will contain the originals and the preservation copies as if Archivematica had normalized for preservation AND
- [ ] the AIP will include normalization events

### 9.11

**Severity**: Medium

When a transfer is processed with "Generate thumbnails" set to Yes, without default
- [ ] Then thumbnails will be created for all digital objects in the AIP where meaningful thumbnails can be created AND
- [ ] Thumbnails will not be created if the thumbnail would be a default icon

### 9.12

**Severity**: Medium

When a transfer is processed with "Generate thumbnails" set to No
- [ ] Then no thumbnails will be created

### 9.13

**Severity**: Medium

**External tools**: Tesseract

Given that a transfer contains a file that can be transcribed (*SampleTransfers/OCRImage*)

When a transfer is processed with "Transcribe files (OCR)" set to Yes
- [ ] Then the Transcription microservice will complete successfully AND
- [ ] the AIP will contain a text file of the transcribed contents in the /metadata/OCRfiles/ directory

## 10 - Performance & Resilience

### 10.1

**Severity**: Medium

When multiple transfers are started at the same time
- [ ] Then Archivematica should gracefully handle processing multiple transfers at the same time
(Note: this assumes that the Archivematica machine has enough memory and power to process the transfers; these metrics can be be scaled up significantly as needed.)

### 10.2

**Severity**: Medium

When a transfer with a large number of files is processed
- [ ] Then Archivematica should process the individual files in the transfer as normal
(Note: this assumes that the Archivematica machine has enough memory and power to process the transfer; these metrics can be be scaled up significantly as needed.)

### 10.3

**Severity**: Medium

When a large transfer is processed (20Gb+)
- [ ] Then Archivematica should process the transfer as usual
(Note: this assumes that the Archivematica machine has enough memory and power to process the transfer; these metrics can be be scaled up significantly as needed.)

### 10.4

**Severity**: Medium

When a user clicks on the Remove button for a single completed transfer/SIP on the Transfer or Ingest tab
- [ ] Then a popup will allow the user to confirm that they want to remove the transfer/SIP AND
- [ ] the transfer will no longer appear in the Transfer or Ingest tab

### 10.5

**Severity**: Medium

When a user clicks on the Remove button for all transfers/SIPs on the Transfer or Ingest tab
- [ ] Then a popup will allow the user to confirm that they want to remove all transfers/SIPs AND
- [ ] all transfers/SIPs that have completed successfully or failed will no longer appear in the Transfer or Ingest tab AND
- [ ] Transfers/SIPs that were rejected or are still in progress will remain in the Transfer or Ingest tab

## 11 - Add Metadata

### 11.1

**Severity**: Medium

Given that a user wants to record rights metadata for the transfer using the GUI form

When they click on the metadata icon for a transfer/SIP proir to the metadata reminder microservice
- [ ] Then they can add, edit, and delete metadata using the GUI form AND
- [ ] The metadata will be written to the METS

### 11.2

**Severity**: High

Given that a user wants to record descriptive metadata for the transfer using the GUI form

When they click on the metadata icon for a transfer/SIP proir to the metadata reminder microservice
- [ ] Then they can add, edit, and delete metadata using the GUI form AND
- [ ] The metadata will be written to the METS

### 11.3

**Severity**: High

Given that the accession number field is filled out for a new transfer

When the transfer is processed
- [ ] Then the accession number will end up in METS as a registration event outcome detail note.

## 12 - Backlog

### 12.1

**Severity**: High

Given that a user has sent a transfer to backlog at “Job: Create SIP(s)?"

When the user downloads the transfer from the backlog
- [ ] Then the package that is downloaded from the backlog will be a valid bag AND
- [ ] it will contain a transfer METS file

### 12.2

**Severity**: High

Given that a transfer is in the backlog

When the user searches the backlog using the search interface on the Backlog tab
- [ ] Then searches should be successful across all search parameters (file name, file extension, accession number, ingest date, SIP UUID)
(Note: some search parameters require keyword vs phrase or vice versa; searching is case sensitive)

### 12.3

**Severity**: Medium

Given that a transfer is in the backlog

When the user creates a delete request and the delete request is approved in the Storage Service
- [ ] Then the transfer should be removed from the backlog

## 13 - Appraisal

### 13.1

**Severity**: High

Given that a transfer is in the backlog

When the user searches using the search interface on the Appraisal tab
- [ ] Then searches should be successful across all search parameters (file name, file extension, accession number, ingest date, SIP UUID) AND
- [ ] the search results should be displayed in the backlog pane
(Note: some search parameters require keyword vs phrase or vice versa; searching is case sensitive)

### 13.2

**Severity**: Medium

Given that the user has searched for some material to populate the backlog pane

When the user selects Collapse all/Expand all
- [ ] Then all directories should collapse or expand

### 13.3

**Severity**: Medium

Given that a user has selected several files in the Backlog pane

When the user selects Deselect all
- [ ] Then the files should be deselected

### 13.4

**Severity**: Medium

Given that a user has selected several files in the Backlog pane

When they add a tag to the selected files
- [ ] Then the tags added to the items should be visible in backlog pane as well as in dropdown AND
- [ ] The tags should be visible in the Analysis pane's Tags tab AND
- [ ] The tags should be visible in the File list pane AND
- [ ] The user can create a SIP using the tags from the Arrangement pane

### 13.5

**Severity**: Medium

Given that a user has added tags to several items

When they create a SIP from the tags in the Arrangement tab
- [ ] Then the SIP should be started AND
- [ ] the SIP should automatically appear on the Ingest tab

## 14 - Access integrations

### 14.1

**Severity**: High

Given that the AtoM integration is configured

When a user uploads a DIP to AtoM
- [ ] Then the digital objects will be uploaded to the AtoM target description

### 14.2

**Severity**: High

Given that a transfer contains Dublin Core descriptive metadata for individual objects

When the user uploads the DIP to AtoM
- [ ] Then the descriptive metadata will be uploaded to the appropriate target description in AtoM
(Note: collection-level description if aggregate metadata provided; object-level description if individual object metadata provided)

### 14.3

**Severity**: Medium

Given that a user has arranged digital objects/directories using the Arrangement pane of the Appraisal tab

When the DIP is uploaded to AtoM
- [ ] Then the arrangement should be reflected in AtoM AND
- [ ] a logical structMap reflecting the arrangement will be created in the METS

### 14.4

**Severity**: Medium

Given that a user has applied levels of description to digital objects/directories using the Arrangement pane of the Appraisal tab

When the DIP is uploaded to AtoM
- [ ] Then the levels of description should be reflected in AtoM AND
- [ ] a logical structMap reflecting the arrangement will be created in the METS

### 14.5

**Severity**: Medium

Given that a user has added a valid AtoM slug to the access system ID box in the transfer widget

When the DIP is uploaded to AtoM
- [ ] Then Archivematica should not prompt the user to enter the slug during the Upload DIP microservice AND
- [ ] the digital objects will be uploaded to the AtoM target description

### 14.6

**Severity**: Medium

Given that a transfer includes a metadata.csv

When "Upload DIP to CONTENTdm" is selected during the Upload DIP microservice
- [ ] Then a simple.txt or compound.txt file will be added to the DIP AND
- [ ] the simple.txt/compound.txt file will contain the descriptive metadata from the CSV

## 15 - Archival Storage

### 15.1

**Severity**: Medium

Given that an AIP has been stored

When the user wants to upload the digital object metadata for the AIP objects to an AtoM description
- [ ] Then the user can navigate to the AIP information page AND
- [ ] the user can use the Upload DIP action at the bottom of the page by entering the slug for the AtoM description into the *Insert slug* textbox and clicking *Upload* AND
- [ ] archival descriptions will be created in AtoM that contain the digital object metadata, but no digital objects

### 15.2

**Severity**: Medium

Given that a transfer/SIP is at a decision point where rejecting is an option

When the user selects to reject the transfer/SIP
- [ ] Then the reject microservice will complete successfully AND
- [ ] the AIP is sent to the rejected directory AND
- [ ] the AIP can be accessed from the rejected directory

### 15.3

**Severity**: High

Given that there are AIPs in storage

When the user does a search with "Show files?" selected
- [ ] These "Select columns" options also apply to the “Show files” display option (except “AIC”, “File Count” “Created”, and “Encrypted”).

### 15.4

**Severity**: Medium

Given that the user has done a search in the Archival Storage tab

When the user clicks on "Create an AIC"
- [ ] The select and deselect choices persist between user sessions.

### 15.5

**Severity**: High

Given that an AIP has been stored and the user has navigated to the AIP storage page

When the user clicks on "Download"
- [ ] Then the AIP should be downloaded

### 15.6

**Severity**: Medium

Given that an AIP has been stored and the user has navigated to the AIP storage page

When the user clicks on "View" to view the METS file
- [ ] Then the METS file should be downloaded

### 15.7

**Severity**: Medium

Given that an AIP has been stored and the user has navigated to the AIP storage page

When the user clicks on "View" to view the pointer file
- [ ] Then the pointer file should be downloaded

### 15.8

**Severity**: High

**Current coverage in AMAUAT**: Ok / Implicit (test does not include adding metadata)

**AMAUAT tests**: reingest-aip.feature

Given that an AIP has been stored

When the user selects "Metadata re-ingest" from the AIP information page
- [ ] Then the AIP will be sent to the Ingest tab where re-ingest can be approved AND
- [ ] the microservices and jobs will follow the selected processing configuration AND
- [ ] metadata can be added using the metadata icon in the GUI AND
- [ ] the new AIP over-writes the old one in storage
- [ ] <premis:eventType>reingestion</premis:eventType> is present in the resulting METS

### 15.9

**Severity**: High

**Current coverage in AMAUAT**: Ok / Implicit (test does not specify DIP creation)

**AMAUAT tests**: reingest-aip.feature

Given that an AIP has been stored

When the user selects "Partial re-ingest" from the AIP information page
- [ ] Then the AIP will be sent to the Ingest tab where re-ingest can be approved AND
- [ ] the microservices and jobs will follow the selected processing configuration AND
- [ ] the user can select a different normalization option than the first time (i.e. can create a DIP on demand)
- [ ] the new AIP over-writes the old one in storage
- [ ] <premis:eventType>reingestion</premis:eventType> is present in the resulting METS

### 15.10

**Severity**: High

Given that an AIP has been stored

When the user requests deletion of the AIP from the AIP information page
- [ ] Then the status of the AIP will be "Deletion requested"
(See 24.2 for other half of the deletion test)

### 15.11

Given that an encrypted storage location exists

When an AIP is stored in the encrypted storage location
- [ ] Then the AIP pointer file will include an encryption event and public key AND
- [ ] the AIP can be downloaded AND
- [ ] the AIP can be reingested and downloaded again

### 15.12

Given that a storage location has a replicator location connected to it

When an AIP is stored in the storage location
- [ ] Then the AIP will be saved in the storage location AND
- [ ] a second copy of the AIP will be saved in the replicator location

## 16 - Preservation Planning

### 16.1

**Severity**: Medium

Given that the file identification command is set to Siegfried

When the user enables Fido
- [ ] Then the Siegfried command will be disabled AND
- [ ] the Fido command will be enabled AND
- [ ] when file identification runs next, Fido will be used instead of Siegfried

### 16.2

**Severity**: High

Given that the user has disabled a command

When a transfer that would normally call that command is processed
- [ ] Then the command will not run AND
- [ ] the task output will not show that the command has run AND
- [ ] the METS file will not show that the command was run AND
- [ ] the command can be re-enabled later

### 16.3

**Severity**: Medium

Given that a user has edited a command

When a transfer that calls the command is processed
- [ ] Then the edited version of the command will run AND
- [ ] the task output and METS will show that the updated command ran, if applicable

### 16.4

**Severity**: High

Given that a user has edited a command

When the user wants to revert to the previous command
- [ ] Then the user can click on "Revision history" AND
- [ ] the user can select the previous version that they would like to revert to AND
- [ ] the task output and METS will show that the reverted version of the command was run, if applicable

## 17 - Administration

### 17.1

**Severity**: High

Given that the user is on the Administration tab > Processing configuration

When the user selects "Edit"
- [ ] Then the processing configuration form will open AND
- [ ] the user will be able to make changes AND
- [ ] the user can save the form

### 17.2

**Severity**: High

Given that the user has changed some values in the default processing configuration

When a transfer is started from the dashboard
- [ ] Then the transfer should follow the decisions as set in the default processing configuration

### 17.3

**Severity**: Medium

Given that the user is on the Administration tab > Processing configuration

When the user selects "Download"
- [ ] Then an XML file containing the processing configuration decisions set in the config form will be downloaded

### 17.4

**Severity**: Medium

Given that the user has changed some values in the default processing configuration

When the user selects "Reset"
- [ ] Then the configuration will be reset to the standard Archivematica pre-sets (see docs for pre-set info https://www.archivematica.org/en/docs/latest/user-manual/administer/dashboard-admin/#processing-config-fields)

### 17.5

**Severity**: Medium

Given that the user is on the Administration tab > Processing configuration

When the user selects "Add"
- [ ] Then a processing configuration form will open AND
- [ ] the user can select decision points AND
- [ ] the user can save the form

### 17.6

Given that the user is on the Administration tab > Storage locations

When the user increases or decreases the amount of material in a given storage location
- [ ] Then the Used storage value will increase or decrease correspondingly

### 17.7

**Severity**: Medium

Given that the user is on the Administration tab > Processing storage usage

When the user selects "Calculate disk usage”
- [ ] Then the disk usage will be calculated and displayed

### 17.8

**Severity**: Medium

Given that the user is on the Administration tab > Processing storage usage and has calculated disk usage

When the user selects "Clear" for one of the storage locations
- [ ] Then the user will be prompted to confirm the choice AND
- [ ] the folder will be cleared AND
- [ ] the usage will reset to 4.0KB

### 17.9

**Severity**: High

Given that the credentials have been added to the DIP Upload page for an AtoM, Binder, or ArchivesSpace instance

When the user uploads a DIP to those systems
- [ ] Then DIP upload will be successful

### 17.10

**Severity**: High

Given that the user has changed a language in Administration > Languages

When the user views the dashboard
- [ ] Then the microservice tasks and interface items should appear in that language (translation completeness permitting)

### 17.11

**Severity**: Medium

When the user checks the version on Administration > Version
- [ ] Then the version number should be correct AND
- [ ] the Agent code should correspond with the version

## 18 - Users & Permissions

### 18.1

**Severity**: High

Given that a user is an administrator

When the user goes to Administration > Users
- [ ] Then the user will be able to add a new user, edit an existing user, or delete a user

### 18.2

**Severity**: High

Given that a user is not an administrator

When the user goes to the Administration tab
- [ ] Then the user will not see the Users menu item

### 18.3

**Severity**: Medium

When LDAP is configured


### 18.4

**Severity**: Medium

When CAS is configured
- [ ] Then attempting to access Archivematica in the browser when not yet authenticated redirects the user to a CAS server for authentication AND
- [ ] After successfully authenticating on the CAS server, the user is logged into Archivematica AND
- [ ] A new user account is created for the user if one did not already exist AND
- [ ] Logging out from Archivematica ends the Archivematica session and logs the user out on the CAS server

## 19 - Failure Reports & Notifications

### 19.1

**Severity**: High

Given that a transfer has failed

When the user views Administration > Failures
- [ ] Then the user will see a failure report AND
- [ ] the user can click on the report to see which job failed AND
- [ ] the user can delete the failure report

### 19.2

**Severity**: High

Given that a user has a valid email address

When a transfer fails
- [ ] Then the user will receive an emailed version of the failure report

## 20 - System Config Options

### 20.1

**Severity**: Medium

Given that indexing has been disabled for a pipeline

When the user opens the dashboard
- [ ] Then the Backlog, Appraisal, and Archival storage tabs are not visible
- [ ] the Index AIP job will not run (task output will read `Skipping indexing: AIPs indexing is currently disabled.`)

## 21 - Storage Service

### 21.1

**Severity**: High

Given that Fixity has been configured

When the user views the Packages tab of the Storage Service
- [ ] Then the user will see data in the Fixity Date and Fixity Status columns AND
- [ ] The information in those columns will be correct

### 21.2

**Severity**: High

Given that there is a DIP in storage

When the user deletes the DIP from the Packages tab
- [ ] Then the DIP will be deleted successfully

### 21.3

**Severity**: Medium

AIP Recovery


### 21.4

**Severity**: High

Given that a user has requested that an AIP be deleted using the Delete interface in the dashboard

When a Storage Service admin approves the Deletion requests in the Storage Service
- [ ] Then the AIP will be deleted AND
- [ ] the entry for the AIP will be removed from the Archival Storage tab in the dashboard AND
- [ ] a record of the decision will appear in the Closed requests table

### 21.5

**Severity**: High

Given that a user has requested that an AIP be deleted using the Delete interface in the dashboard

When a Storage Service admin rejects the Deletion requests in the Storage Service
- [ ] Then the AIP will not be deleted AND
- [ ] the AIP's status the Archival Storage tab in the dashboard will be set back to Stored AND
- [ ] a record of the decision will appear in the Closed requests table

## 22 - METS Validation

### 22.1

**Severity**: High

**External tools**: METS-RW

Given that an AIP METS file has been created

When the user validates the METS file against the PREMIS in METS Toolbox validator (http://pim.fcla.edu/validate) or against another online validator such as https://www.freeformatter.com/xml-validator-xsd.html
- [ ] Then no errors are reported AND
- [ ] The validation is successful

### 22.2

**Severity**: High

**Current coverage in AMAUAT**: Ok / Implicit (test does not specify all METS/PREMIS sections)

**AMAUAT tests**: transfer-microservices.feature

**External tools**: METS-RW

Given that an AIP METS file has been created

When the user validates the METS file against the Archivematica METS profile (created by Evelyn, not hosted anywhere yet...)
- [ ] Then the expected METS and PREMIS sections are present and they match expected values.
