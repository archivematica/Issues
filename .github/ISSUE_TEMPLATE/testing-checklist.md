---
name: Testing checklist template
about: Use this template to create an issue for regression testing
---
## 1 - Transfer Types

### 1.1

**Sev**: High

**Current coverage in AMAUAT**: Excellent

**AMAUAT tests**: create-aip.feature

**External tools**: null

When *SampleTransfers/Images* is processed using the Standard transfer type
- [ ] All microservices execute successfully
- [ ] All standard AIP structure and METS structure criteria apply

### 1.2

**Sev**: null

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

When *SampleTransfer/ZippedDirectoryTransfers/DemoTransferCSV.zip* is processed using the Zipped Directory transfer type
- [ ] The Extract zipped bag transfer job executes successfully
- [ ] All microservices execute successfully
- [ ] All standard AIP structure and METS structure criteria apply

### 1.3

**Sev**: High

**Current coverage in AMAUAT**: Excellent

**AMAUAT tests**: create-aip.feature

**External tools**: null

When *SampleTransfers/UnzippedBag* is processed using the Unzipped Bag transfer type
- [ ] The 'Verify bag, and restructure for compliance' job in the 'Approve Transfer' microservice executes successfully AND
- [ ] All standard AIP structure and METS structure criteria apply AND
- [ ] The contents of bag-info.txt (if any) are parsed into METS

### 1.4

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: 7zip

When *SampleTransfer/ZippedBag.zip* is processed using the Zipped Bag transfer type
- [ ] The Bag Verification microservice executes successfully AND
- [ ] All standard AIP structure and METS structure criteria apply AND
- [ ] The contents of bag-info.txt (if any) are parsed into METS

### 1.5

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When *SampleTransfer/DSpaceExport* (or one of the zips contained inside) is processed using the DSpace transfer type
- [ ] The Identify DSpace files microservice executes successfully AND
- [ ] All standard AIP structure and METS structure criteria apply

### 1.6

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: tsk_recover (Sleuthkit), unrar-free

When *SampleTransfer/ISODiskImage* is processed using the Disk Image transfer type AND disk image metadata has been added before the transfer is started
- [ ] The disk image metadata ends up in the AIP METS AND
- [ ] All standard AIP structure and METS structure criteria apply

### 1.7

**Sev**: Low

**Current coverage in AMAUAT**: Excellent

**AMAUAT tests**: create-aip.feature

**External tools**: null

When the three Dataverse sample transfers (*SampleTransfers/Dataverse/AStudyOfMyAfternoonDrinks*, *SampleTransfers/Dataverse/NDSAStaffingReport*, *SampleTransfers/Dataverse/XRayScansOfPolyodonSpathula*) are processed using the Dataverse transfer type AND Archivematica is not set to delete packages after extraction
- [ ] Microservice: parse external files succeeds AND
- [ ] Dataverse metadata is parsed into the METS, e.g. DDI information for title and author AND
- [ ] All standard AIP structure and METS structure criteria apply

## 2 - Transfer Variants

### 2.1

**Sev**: High

**Current coverage in AMAUAT**: Ok / Implicit

**AMAUAT tests**: create-aip.feature

**External tools**: null

When a transfer containing descriptive and rights metadata (*SampleTransfer/DemoTransferCSV*) is processed
- [ ] The AIP METS contains descriptive metadata for each of the objects described in the metadata.csv AND
- [ ] The AIP METS contains rights metadata for each of the objects described in the rights.csv

### 2.2

**Sev**: High

**Current coverage in AMAUAT**: Ok / Implicit

**AMAUAT tests**: null

**External tools**: null

When a Transfer containing Submission Documentation (*SampleTransfer/DemoTransferCSV*) is processed
- [ ] Submission documentation is listed in the METS with fileGrp USE="submissionDocumentation"

### 2.3

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When a transfer containing multi-level descriptive metadata (*SampleTransfer/CSVmultiLevel*) is processed
- [ ] The AIP METS contains descriptive metadata for each of the directories described in the metadata.csv

### 2.4

**Sev**: High

**Current coverage in AMAUAT**: Ok / Implicit

**AMAUAT tests**: null

**External tools**: null

When a transfer containing descriptive metadata for individual files using a metadata.csv (*SampleTransfer/CSVmetadata*) is processed
- [ ] The AIP METS contains descriptive metadata for each of the files described in the metadata.csv

### 2.5

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When a transfer with files that have been manually normalized outside of Archivematica (*TestTransfers/ManualNormalization*) is processed, and "Normalize for preservation and access" is selected at the Normalization microservice
- [ ] Originals should be .dat, .TGA, and .GIF AND
- [ ] Preservation copies should be .prk and .tif (there is no preservation copy made of the GIF) AND
- [ ] Access copies should be .bmp, .jpg, and .jpg.

### 2.6

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

With “Normalization” set to None and “Approve normalization” set to None in the default processing config, process a transfer using *SampleTransfers/AccessCopies*, “Job: Normalize” should only give three options - choose “Normalize for preservation”.
- [ ] Originals should be .png AND
- [ ] No preservation copies should be generated (PNG is already considered a preservation format) AND
- [ ] Access copies should be .gif

### 2.7

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

With “Normalization” set to None and “Approve normalization” set to None in the default processing config, run SampleTransfers/ServiceCopies transfer and choose “Normalize service files for access”.
- [ ] "Job Normalize service files for access" should run AND
- [ ] the task output should show that the service files were used to create access copies.

### 2.8

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When *SampleTransfers/ProcessingMCP* is processed using the Standard transfer type
- [ ] then the Transfer and Ingest processing will follow the decisions set out in the processing configuration XML file, rather than the default configuration

### 2.9

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When *SampleTransfers/BagExamples/SimpleBagWithProcessingMCP* is processed as a Zipped Bag transfer
- [ ] then the Transfer and Ingest processing will follow the decisions set out in the processing configuration XML file, rather than the default configuration

### 2.1

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When one of the directories in *SampleTransfers/StructMapTransferSamples* is processed using the Standard transfer type
- [ ] the provided structural map will be included in the AIP METs file.

### 2.11

**Sev**: null

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a transfer contains a premis.xml file (*SampleTransfers/PremisImporter*)

When the premis.xml file is parsed into the Archivematica METS file
- [ ] Then the PREMIS XML import file's Event and Agent entities are added to the Archivematica AIP METS file AND
- [ ] the Events retain their original field values, including the event details AND
- [ ] the Events are linked to the same Agents as in the PREMIS XML import file

### 2.12

**Sev**: null

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a transfer contains an identifiers.json file (*SampleTransfers/DemoTransferCSV*)

When the identifiers.json file is imported into Archivematica after the Objects are ingested
- [ ] Then the identifiers from the JSON file are mapped as objectIdentifiers in the METS file

## 3 - Checksums & Integrity Checking

### 3.1

**Sev**: High

**Current coverage in AMAUAT**: Excellent

**AMAUAT tests**: checksum.feature

**External tools**: null

When a transfer includes invalid external checksums
(*TestTransfers/fixityCheckShouldFail*)
- [ ] Then the job "Verify metadata directory checksums" on the Transfer tab fails AND
- [ ] the stdout/stderr for the failed job describe which checksums failed AND
- [ ] the "Failed transfer" microservice is triggerd

### 3.2

**Sev**: High

**Current coverage in AMAUAT**: Excellent

**AMAUAT tests**: checksum.feature

**External tools**: null

When a transfer includes valid external checksums
(*SampleTransfers/DemoTransferCSV*)
- [ ] Then the job "Verify metadata directory checksums" on the Transfer tab will complete successfully AND
- [ ] The stdout will read Comparison was OK for each checksum file

## 4 - Virus scanning

### 4.1

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: virus.feature

**External tools**: null

When a transfer containing a virus is processed (*TestTransfers/virusTests*)

- [ ] The job "Scan for viruses" will fail AND
- [ ] The standard streams will report which files failed virus scanning

### 4.2

**Sev**: High

**Current coverage in AMAUAT**: Excellent

**AMAUAT tests**: virus.feature

**External tools**: null

When a transfer that does not contain a virus is processed
- [ ] The job "Scan for viruses" will complete successfully

## 5 - Special Characters

### 5.1

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When a transfer contains files and directories with non-ASCII characters in the file/directory name (*TestTransfers/badNames*)
- [ ] Then the "Change transfer filenames" microservice will complete successfully AND
- [ ] the AIP will contain a name cleanup log AND
- [ ] a name cleanup PREMIS event will be present in the METS

### 5.2

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When the transfer name contains non-ASCII characters
- [ ] Then the "Change transfer filenames" microservice will complete successfully AND
- [ ] the transfer’s name will be changed to use ASCII characters

### 5.3

**Sev**: null

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

When a transfer contains files with non-ASCII characters in the file name as well as a metadata.csv file (*SampleTransfers/DiacriticsTest*)
- [ ] Then the "Change transfer filenames" microservice will complete successfully AND
- [ ] the AIP will contain a name cleanup log AND
- [ ] a name cleanup PREMIS event will be present in the METS AND

## 6 - File Identification

### 6.1

**Sev**: High

**Current coverage in AMAUAT**: Excellent

**AMAUAT tests**: null

**External tools**: Siegfried

Given that Siegfried is set as the file identification tool

When a transfer is processed
- [ ] Then Siegfried is able to identify file formats and versions accurately AND
- [ ] one <premis:eventType>format identification</premis:eventType> for each file will be present in the METS
- [ ] the premis:eventDetail will indicate that Siegfried was the tool used

### 6.2

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: Siegfried

Given that Siegfried is set as the file identification tool

AND the Processing Configuration in the Administration settings has "Perform file format identification (Transfer)" set to Yes

When a transfer that includes known formats is processed (e.g. *SampleTransfers/Images*)
- [ ] Then Siegfried successfully identifies the formats during the *Identify File Format* microservice

### 6.3

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: Siegfried

Given that Siegfried is set as the file identification tool

When a transfer includes a format that is unknown to Siegfried (try sampleTransfers/Multimedia) and is processed with "Perform file format identification (Transfer)" set to Yes
- [ ] Then Job: Identify file format shows as failed in the dashboard AND
- [ ] The stderr shows which file cannot be identified AND
- [ ] The premis:formatName field for the premis Object has a value of unknown AND
- [ ] There is no format identification Event for the file

### 6.4

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: Fido

Given that Fido is set as the file identification tool

When a transfer is processed with "Perform file format identification (Transfer)" set to Yes
- [ ] Then Fido is able to identify file formats and versions accurately AND
- [ ] one <premis:eventType>format identification</premis:eventType> for each file will be present in the METS
- [ ] the premis:eventDetail will indicate that Fido was the tool used

### 6.5

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: Fido

Given that Fido is set as the file identification tool

AND the Processing Configuration in the Administration settings has "Perform file format identification (Transfer)" set to Yes

When a transfer that includes known formats is processed (e.g. *SampleTransfers/Images*)
- [ ] Then Fido successfully identifies the formats during the *Identify File Format* microservice

### 6.6

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: Fido

Given that Fido is set as the file identification tool

When a transfer includes a format that is unknown to Fido is processed with "Perform file format identification (Transfer)" set to Yes
- [ ] Then Job: Identify file format shows as failed in the dashboard AND
- [ ] The stderr shows which file cannot be identified AND
- [ ] The premis:formatName field for the premis Object has a value of unknown AND
- [ ] There is no format identification Event for the file

### 6.7

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: File extension script

Given that File Extension is set as the file identification tool

When a transfer is processed with "Perform file format identification (Transfer)" set to Yes
- [ ] Then the format should be identified based on its file extension AND
- [ ] a format identification PREMIS event is created AND
- [ ] the premis:eventDetail indicates that File Extension version="0.1" was the tool used

### 6.8

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When a transfer is processed with "Perform file format identification (Transfer)" set to No
- [ ] Then the standard output for the job "Identify file format" will be "Skipping file format identification" AND
- [ ] there will be no format identification PREMIS events for the transfer objects in the METS

## 7 - Package Extraction

### 7.1

**Sev**: High

**Current coverage in AMAUAT**: Excellent

**AMAUAT tests**: extract-package.feature

**External tools**: null

When a transfer containing a package (*SampleTransfers/OfficeDocs*) is processed with the extract packages option set to Yes
- [ ] The job "Extract contents from compressed archives" completes successfully AND
- [ ] a directory with the same name as the package + the timestamp of the unpacking event is created to contain the extracted contents AND
- [ ] sanitization, virus scanning, and file identification are run on the extracted contents AND
- [ ] the extracted contents are checked for further packages, which are then extracted &etc. AND
- [ ] an unpacking PREMIS event is created

### 7.2

**Sev**: Medium

**Current coverage in AMAUAT**: Excellent

**AMAUAT tests**: extract-package.feature

**External tools**: null

When a transfer containing a broken package (*TestTransfers/broken_package_format_types*) is processed with the extract packages option set to Yes
- [ ] The job "Extract contents from compressed archives" will fail (note: dashboard shows a success; known issue) AND
- [ ] the standard output indicates which file caused the job to fail AND
- [ ] the "Failed transfer" microservice will be triggered

### 7.3

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When a transfer containing a package (*SampleTransfers/OfficeDocs*) is processed with "Extract packages" set to Yes and "Delete packages after extraction" set to Yes
- [ ] The resulting AIP will not contain the original package

### 7.4

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When a transfer containing a package (*SampleTransfers/OfficeDocs*) is processed with "Extract packages" set to Yes and "Delete packages after extraction" set to No
- [ ] The resulting AIP will contain the original package

## 8 - Characterization

### 8.1

**Sev**: High

**Current coverage in AMAUAT**: TBC - need to check which tools we use now

**AMAUAT tests**: null

**External tools**: FFprobe, ExifTool, MediaInfo, FITS, fiwalk (Sleuthkit)

When a transfer is processed
- [ ] Then the "Characterize and extract metadata" microservice will run AND
- [ ] the appropriate characterization tool for a given format will be triggered AND
- [ ] the characterization tool outputs will be captured in the premis:objectCharacteristicsExtension container

## 9 - Validation

### 9.1

**Sev**: High

**Current coverage in AMAUAT**: Excellent

**AMAUAT tests**: null

**External tools**: JHOVE

When a transfer containing files that can be validated by JHOVE (*SampleTransfers/Images*) is processed
- [ ] Then the job "Validate formats" will complete successfully AND
- [ ] it will contain accurate validation information for a given format AND
- [ ] one <premis:eventType>validation</premis:eventType> for each file will be present in the METS AND
- [ ] the premis:eventDetail for the validation event will indicate that JHOVE was the tool used

### 9.2

**Sev**: Medium

**Current coverage in AMAUAT**: TBC

**AMAUAT tests**: null

**External tools**: MediaConch

When a transfer containing Matroska files (*SampleTransfers/Matroska*) is processed
- [ ] Then the job "Validate formats" will complete successfully AND
- [ ] it will contain accurate validation information for the Matroska files AND
- [ ] one <premis:eventType>validation</premis:eventType> for each file will be present in the METS AND
- [ ] the premis:eventDetail for the validation event will indicate that MediaConch was the tool used

### 9.3

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: MediaConch

Given that a MediaConch policy has been created and added to Archivematica

When a transfer containing material that meets the policy criteria is processed with "Perform policy checks on originals" set to Yes
- [ ] Then the policy check will complete successfully AND
- [ ] a validation PREMIS event for the policy check will be created

## 10 - Examine contents

### 10.1

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: Bulk Extractor

Given that a transfer contains a file containing personally identifying information (*SampleTransfers/DemoTransferCSV*)

When a transfer is processed with "Examine contents" set to Yes
- [ ] Then the Examine contents microservice will complete successfully AND
- [ ] the AIP will contain Bulk Extractor logs
(See also: 14.7)

## 11 - Normalization

### 11.1

**Sev**: High

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a transfer contains file formats for which there are preservation and access normalization rules
When the user selects "normalize for preservation and access" at the Normalize job

- [ ] Then the files will be normalized for preservation and access as per the rules AND
- [ ] the preservation derivatives will be added to the AIP with a UUID suffix and the appropriate file extension AND
- [ ] the access derivatives will be added to the DIP AND
- [ ] normalization premis events will be added to the METS

### 11.2

**Sev**: High

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a transfer contains file formats for which there are preservation normalization rules

When the user selects "normalize for preservation" at the Normalize job

- [ ] Then the files will be normalized for preservation as per the rules AND
- [ ] the preservation derivatives will be added to the AIP with a UUID suffix and the appropriate file extension AND
- [ ] normalization premis events will be added to the METS

### 11.3

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a transfer contains service files (*SampleTransfers/ServiceCopies*)

When the user selects "normalize service files for access" at the Normalize job
- [ ] Then the service files be used to create the access derivatives AND
- [ ] the access derivatives will be added to the DIP

### 11.4

**Sev**: High

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a transfer contains file formats for which there are normalization rules

When the user selects "do not normalize" at the Normalize job
- [ ] Then normalization will not occur AND
- [ ] the AIP will contain originals only

### 11.5

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a user selects "normalize manually" at the Normalize job

When the user manually inserts normalized files into the SIP (by accessing the pipeline's processing location directly via SSH or SFTP) using the required directory structure (see documentation)

And then selects "Approve" at the Approve normalization job
- [ ] The "Process manually normalized files" will be completed successfully AND
- [ ] the preservation derivatives will be added to the AIP with a UUID suffix and the appropriate file extension AND
- [ ] the access derivatives will be added to the DIP

### 11.6

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that the user has manually normalized the files as per 9.1.5

When the user clicks on the metadata icon and then "Manual normalization event detail"
- [ ] Then the user will be able to enter normalization event information for the manual normalization action AND
- [ ] the event information will be added to the METS

### 11.7

**Sev**: High

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a transfer contains file formats for which there are access normalization rules

When the user selects "normalize for access" at the Normalize job
- [ ] Then access derivatives will be created and added to the DIP AND
- [ ] the AIP will contain originals only

### 11.8

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a transfer includes an access directory with manually normalized access derivatives (*SampleTransfers/AccessCopies*)

When the user reaches the Normalize job
- [ ] Then the dropdown will only have two normalization options ("Normalize for preservation" and "Do not normalize") AND
- [ ] regardless of the option picked, a DIP will be created with the access copies from the transfer

### 11.9

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a transfer includes a preservation directory with manually normalized preservation derivatives (*SampleTransfers/PreservationCopies*)

When the user reaches the Normalize job and chooses "Normalize for Preservation"
- [ ] Then normalization will not occur during the Normalization microservice AND
- [ ] the "Process manually normalized files" microservice will recognize the manualNormalization/preservation directory AND
- [ ] UUIDs will be assigned to the preservation copies and included in their filenames AND
- [ ] the AIP will contain the originals and the preservation copies as if Archivematica had normalized for preservation AND
- [ ] the AIP will include normalization events

### 11.1

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: convert (ImageMagick)

When a transfer is processed with "Generate thumbnails" set to Yes
- [ ] Then thumbnails will be created for all digital objects in the AIP

### 11.11

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

When a transfer is processed with "Generate thumbnails" set to Yes, without default
- [ ] Then thumbnails will be created for all digital objects in the AIP where meaningful thumbnails can be created AND
- [ ] Thumbnails will not be created if the thumbnail would be a default icon

### 11.12

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

When a transfer is processed with "Generate thumbnails" set to No
- [ ] Then no thumbnails will be created

### 11.13

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: Tesseract

Given that a transfer contains a file that can be transcribed (*SampleTransfers/OCRImage*)

When a transfer is processed with "Transcribe files (OCR)" set to Yes
- [ ] Then the Transcription microservice will complete successfully AND
- [ ] the AIP will contain a text file of the transcribed contents in the /metadata/OCRfiles/ directory

## 12 - Performance & Resilience

### 12.1

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When multiple transfers are started at the same time
- [ ] Then Archivematica should gracefully handle processing multiple transfers at the same time
(Note: this assumes that the Archivematica machine has enough memory and power to process the transfers; these metrics can be be scaled up significantly as needed.)

### 12.2

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When a transfer with a large number of files is processed
- [ ] Then Archivematica should process the individual files in the transfer as normal
(Note: this assumes that the Archivematica machine has enough memory and power to process the transfer; these metrics can be be scaled up significantly as needed.)

### 12.3

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When a large transfer is processed (20Gb+)
- [ ] Then Archivematica should process the transfer as usual
(Note: this assumes that the Archivematica machine has enough memory and power to process the transfer; these metrics can be be scaled up significantly as needed.)

### 12.4

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When a user clicks on the Remove button for a single completed transfer/SIP on the Transfer or Ingest tab
- [ ] Then a popup will allow the user to confirm that they want to remove the transfer/SIP AND
- [ ] the transfer will no longer appear in the Transfer or Ingest tab

### 12.5

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When a user clicks on the Remove button for all transfers/SIPs on the Transfer or Ingest tab
- [ ] Then a popup will allow the user to confirm that they want to remove all transfers/SIPs AND
- [ ] all transfers/SIPs that have completed successfully or failed will no longer appear in the Transfer or Ingest tab AND
- [ ] Transfers/SIPs that were rejected or are still in progress will remain in the Transfer or Ingest tab

### 12.6

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

We could add a variety of failure scenarios here -- e.g. if SS is down? or elasticSearch etc?
null

## 13 - Add Metadata

### 13.1

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user wants to record rights metadata for the transfer using the GUI form

When they click on the metadata icon for a transfer/SIP proir to the metadata reminder microservice
- [ ] Then they can add, edit, and delete metadata using the GUI form AND
- [ ] The metadata will be written to the METS

### 13.2

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user wants to record descriptive metadata for the transfer using the GUI form

When they click on the metadata icon for a transfer/SIP proir to the metadata reminder microservice
- [ ] Then they can add, edit, and delete metadata using the GUI form AND
- [ ] The metadata will be written to the METS

### 13.3

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the accession number field is filled out for a new transfer

When the transfer is processed
- [ ] Then the accession number will end up in METS as a registration event outcome detail note.

## 14 - Backlog

### 14.1

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user has sent a transfer to backlog at “Job: Create SIP(s)?"

When the user downloads the transfer from the backlog

- [ ] Then the package that is downloaded from the backlog will be a valid bag AND
- [ ] it will contain a transfer METS file

### 14.2

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a transfer is in the backlog

When the user searches the backlog using the search interface on the Backlog tab
- [ ] Then searches should be successful across all search parameters (file name, file extension, accession number, ingest date, SIP UUID)
(Note: some search parameters require keyword vs phrase or vice versa; searching is case sensitive)

### 14.3

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a transfer is in the backlog

When the user creates a delete request and the delete request is approved in the Storage Service
- [ ] Then the transfer should be removed from the backlog

## 15 - Appraisal

### 15.1

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a transfer is in the backlog

When the user searches using the search interface on the Appraisal tab
- [ ] Then searches should be successful across all search parameters (file name, file extension, accession number, ingest date, SIP UUID) AND
- [ ] the search results should be displayed in the backlog pane
(Note: some search parameters require keyword vs phrase or vice versa; searching is case sensitive)

### 15.2

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the user has searched for some material to populate the backlog pane

When the user selects Collapse all/Expand all
- [ ] Then all directories should collapse or expand

### 15.3

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user has selected several files in the Backlog pane

When the user selects Deselect all
- [ ] Then the files should be deselected

### 15.4

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user has selected several files in the Backlog pane

When they add a tag to the selected files
- [ ] Then the tags added to the items should be visible in backlog pane as well as in dropdown AND
- [ ] The tags should be visible in the Analysis pane's Tags tab AND
- [ ] The tags should be visible in the File list pane AND
- [ ] The user can create a SIP using the tags from the Arrangement pane

### 15.5

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user has added tags to several items

When they click on the minus sign to remove the tag in the Backlog pane or File list pane
- [ ] Then the tags should be removed AND
- [ ] the tag count in the Analysis pane should update accordingly

### 15.6

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a user has added tags to several items

When they create a SIP from the tags in the Arrangement tab
- [ ] Then the SIP should be started AND
- [ ] the SIP should automatically appear on the Ingest tab

### 15.7

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user has selected several files in the Backlog pane

When the user opens the Report on the Analysis pane > Objects
- [ ] Then the report should list all selected formats AND
- [ ] the report should update accurately when files are selected/deselected

### 15.8

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user has selected several files in the Backlog pane

When the user opens the Visualizations on the Analysis pane > Objects
- [ ] Then the pie chart should show all selected formats by total number of files or by total size of files AND
- [ ] the visualization should update accurately when files are selected/deselected

### 15.9

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a transfer contains credit card numbers (*SampleTransfers/DemoTransferCSV*) or social security numbers that can be recognized by Bulk Extractor

And the transfer was processed with "Examine contents" set to Yes

When the user selects PII or Credit card numbers on the Analysis pane > Examine contents
- [ ] Then a list of files that contain credit card numbers or social security numbers will be displayed

### 15.1

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the user has selected a browser-renderable file (image, audio, video) on the File list pane

When the user selects Preview File on the Analysis pane
- [ ] Then the file should be displayed appropriately in the preview window AND
- [ ] the user should be able to expand file preview pane for an image if using Firefox AND
- [ ] non-previewable files should download for preview

### 15.11

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When the user selects "Show path" in the File list pane
- [ ] Then the path column will be toggled on or off AND
- [ ] The path will contain the full filepath of the file

### 15.12

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that there is material in the backlog

When the user clicks on "Add directory" in the Arrangement pane
- [ ] Then a popup window will allow the user to enter the directory name AND
- [ ] the directory will appear in the Arrangement pane AND
- [ ] the user can drag files from the Backlog pane to the new directory

### 15.13

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that there is a directory in the Arrangement pane

When the user selects the directory and then clicks on "Add directory"
- [ ] Then a popup window will allow the user to enter the directory name AND
- [ ] the directory will appear in the Arrangement pane as a subdirectory of the first directory AND
- [ ] the user can drag files from the Backlog pane to the new directory

### 15.14

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that there is a directory structure in the Arrangement pane

When the user wants to navigate through the directories
- [ ] Then the user can click on the yellow folder icon to navigate through directories

### 15.15

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that there is a directory in the Arrangement pane

When the user selects a file and then clicks on "Edit Metadata"
- [ ] Then a popup window will appear where the user can select the AtoM level of description for the directory or file AND
- [ ] when the SIP is finalized and the DIP is sent to AtoM, the level of description will be added to the record in AtoM

### 15.16

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that there are directories/files in the Arrangement pane

When the user selects a directory/file and then clicks on "Delete selected"
- [ ] Then a popup will allow the user to confirm the deletion AND
- [ ] the directory/file will be deleted

### 15.17

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that there are directories/files in the Arrangement pane

When the user selects a directory and clicks on "Create SIP"
- [ ] Then selected directory and contents will be turned into a SIP AND
- [ ] processing will continue on the Ingest tab

### 15.18

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that there are directories/files in the Arrangement pane but things have gone a bit squirrelly

When the user clicks "Reload"
- [ ] Then the Arrangement pane should be reloaded without having to refresh the page

### 15.19

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the ArchivesSpace integration is configured

When a user clicks on "Search ArchivesSpace" in the ArchivesSpace pane
- [ ] Then ArchivesSpace resources should be displayed

### 15.2

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user has selected an ArchivesSpace resource

When the user selects "Add new child record"
- [ ] Then a metadata form will pop up where the user can add metadata AND
- [ ] the child record will appear in the Appraisal tab AND
- [ ] when the arrangement is finalized and the information sent to ArchivesSpace, the child record will be added to ArchivesSpace- [ ]- [ ]
(- [ ]- [ ] if the ArchivesSpace-DSpace integration is configured)
### 15.21

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user has selected an ArchivesSpace resource

When the user selects "Add new digital object"
- [ ] Then a digital object will be created

### 15.22

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user has created a digital object record

When the user drags and drops a file from the backlog pane onto the digital object record
- [ ] Then the file will appear to be attached to the digital object AND
- [ ] when the arrangement is finalized and the information sent to ArchivesSpace, the file information will be added as an Instance- [ ]- [ ]
(- [ ]- [ ] if the ArchivesSpace-DSpace integration is configured)

### 15.23

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the user has selected a resource or child record in the ArchivesSpace pane

When the user selects "Edit rights metadata"
- [ ] Then the user will be taken to a new browser tab where the user can add PREMIS rights metadata AND
- [ ] when the arrangement is finalized and the information sent to ArchivesSpace, the rights metadata will be added to ArchivesSpace- [ ]- [ ]
(- [ ]- [ ] if the ArchivesSpace-DSpace integration is configured)

### 15.24

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the user has selected a resource or child record in the ArchivesSpace pane

When the user selects "Edit metadata"
- [ ] Then a metadata form will pop up will appear where the user can add or edit metadata AND
- [ ] when the arrangement is finalized and the information sent to ArchivesSpace, the metadata will be added to ArchivesSpace- [ ]- [ ]
(- [ ]- [ ] if the ArchivesSpace-DSpace integration is configured)

### 15.25

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the user has selected a child record in the ArchivesSpace pane

When the user selects "Delete selected"
- [ ] Then a popup will appear where the user can confirm the deletion AND
- [ ] when the user confirms the deletion, the child record will be deleted

### 15.26

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the user has created digital object records and attached files to them

When the user selects the parent record and clicks on "Finalize arrangement"
- [ ] Then a SIP should start AND
- [ ] any updated metadata/record structure should be applied in ArchivesSpace AND
- [ ] the digital objects should be added to the ArchivesSpace resources/child records as Instances
- [ ] the material should be added to ArchivesSpace- [ ]- [ ]
(- [ ]- [ ] if the ArchivesSpace-DSpace integration is configured)

## 16 - Access integrations

### 16.1

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the AtoM integration is configured

When a user uploads a DIP to AtoM
- [ ] Then the digital objects will be uploaded to the AtoM target description

### 16.2

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a transfer contains Dublin Core descriptive metadata for individual objects

When the user uploads the DIP to AtoM
- [ ] Then the descriptive metadata will be uploaded to the appropriate target description in AtoM
(Note: collection-level description if aggregate metadata provided; object-level description if individual object metadata provided)

### 16.3

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a user has arranged digital objects/directories using the Arrangement pane of the Appraisal tab

When the DIP is uploaded to AtoM

- [ ] Then the arrangement should be reflected in AtoM AND
- [ ] a logical structMap reflecting the arrangement will be created in the METS

### 16.4

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user has applied levels of description to digital objects/directories using the Arrangement pane of the Appraisal tab

When the DIP is uploaded to AtoM

- [ ] Then the levels of description should be reflected in AtoM AND
- [ ] a logical structMap reflecting the arrangement will be created in the METS

### 16.5

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user has added a valid AtoM slug to the access system ID box in the transfer widget

When the DIP is uploaded to AtoM
- [ ] Then Archivematica should not prompt the user to enter the slug during the Upload DIP microservice AND
- [ ] the digital objects will be uploaded to the AtoM target description

### 16.6

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the Binder integration is configured

When a user creates a DIP and uploads it to Binder
- [ ] Then the DIP will be uploaded to the target artwork or technology record in Binder

### 16.7

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user has added a valid Binder artwork or technology record identifier to the access system ID box in the transfer widget

When the DIP is uploaded to Binder
- [ ] Then Archivematica should not prompt the user to enter the artwork or technology record identifier during the Upload DIP microservice AND
- [ ] the DIP will be uploaded to the Binder target description

### 16.8

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the ArchivesSpace integration is configured

When the user selects "Upload DIP to ArchivesSpace" from the Upload DIP microservice drop-down

- [ ] Then the user will be taken to the ArchivesSpace matching GUI AND
- [ ] the user can search for and navigate through resources AND
- [ ] the user can pair digital objects to resources

### 16.9

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the user has paired a digital object to an ArchivesSpace resource

When the user confirms that matching is complete

- [ ] Then the DIP information will be attached to the ArchivesSpace resource as an Instance

### 16.1

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the transfer includes an ArchivesSpace matching CSV with valid data

When the user selects "Upload DIP to ArchivesSpace" from the Upload DIP microservice drop-down

- [ ] Then the user will be taken to the ArchivesSpace matching GUI AND
- [ ] clicking "Review matches" will show a table of the matches defined in the CSV AND
- [ ] clicking on "Finish matching" will send the DIP information to the ArchivesSpace AND
- [ ] the DIP information will be attached to the ArchivesSpace archival object as an Instance

### 16.11

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a transfer includes a metadata.csv

When "Upload DIP to CONTENTdm" is selected during the Upload DIP microservice
- [ ] Then a simple.txt or compound.txt file will be added to the DIP AND
- [ ] the simple.txt/compound.txt file will contain the descriptive metadata from the CSV

## 17 - Archival Storage

### 17.1

**Sev**: High

**Current coverage in AMAUAT**: Excellent

**AMAUAT tests**: null

**External tools**: null

Given that an AIP storage location has been configured

When a user selects the storage location from the Store AIP dropdown
- [ ] Then the AIP will be stored in the selected storage location

### 17.2

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a transfer/SIP is at a decision point where rejecting is an option

When the user selects to reject the transfer/SIP
- [ ] Then the reject microservice will complete successfully AND
- [ ] the AIP is sent to the rejected directory AND
- [ ] the AIP can be accessed from the rejected directory

### 17.3

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that an AIP has been stored

When the user searches using the search interface on the Archival Storage tab
- [ ] Then searches should be successful across all search parameters (Any, File path, File extension, AIP UUID, AIP name, Identifiers, Part of AIC, AIC identifier, Transfer metadata, Transfer metadata (other)) AND
- [ ] the search results should be displayed in the Archival Storage tab
(Note: some search parameters require keyword vs phrase or vice versa)

### 17.4

**Sev**: High

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that there are AIPs in storage

When the user does a search with "Show files?" selected
- [ ] Then the search results should show individual files

### 17.5

**Sev**: High

**Current coverage in AMAUAT**: Excellent

**AMAUAT tests**: null

**External tools**: null

Given that an AIP has been stored

When the user clicks on the name or UUID of the AIP
- [ ] Then the user should be taken to the AIP information page

### 17.6

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that the user has done a search in the Archival Storage tab

When the user clicks on "Create an AIC"
- [ ] Then a metadata form will open where the user can enter AIC metadata AND
- [ ] once the form is saved, the AIC will appear in the Ingest tab where it can be processed AND
- [ ] the AIC microservices will complete successfully AND
- [ ] the resulting AIC AIP will conform to the criteria for an AIC

### 17.7

**Sev**: High

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that an AIP has been stored and the user has navigated to the AIP storage page

When the user clicks on "Download"
- [ ] Then the AIP should be downloaded

### 17.8

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that an AIP has been stored and the user has navigated to the AIP storage page

When the user clicks on "View" to view the METS file
- [ ] Then the METS file should be downloaded

### 17.9

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that an AIP has been stored and the user has navigated to the AIP storage page

When the user clicks on "View" to view the pointer file
- [ ] Then the pointer file should be downloaded

### 17.10

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that an AIP has been stored

When the user wants to upload the digital object metadata for the AIP objects to an AtoM description
- [ ] Then the user can navigate to the AIP information page AND
- [ ] the user can use the Upload DIP action at the bottom of the page by entering the slug for the AtoM description into the *Insert slug* textbox and clicking *Upload* AND
- [ ] archival descriptions will be created in AtoM that contain the digital object metadata, but no digital objects

### 17.11

**Sev**: High

**Current coverage in AMAUAT**: Ok / Implicit (test does not include adding metadata)

**AMAUAT tests**: reingest-aip.feature

**External tools**: null

Given that an AIP has been stored

When the user selects "Metadata re-ingest" from the AIP information page
- [ ] Then the AIP will be sent to the Ingest tab where re-ingest can be approved AND
- [ ] the microservices and jobs will follow the selected processing configuration AND
- [ ] metadata can be added using the metadata icon in the GUI AND
- [ ] the new AIP over-writes the old one in storage
- [ ] <premis:eventType>reingestion</premis:eventType> is present in the resulting METS

### 17.12

**Sev**: High

**Current coverage in AMAUAT**: Ok / Implicit (test does not specify DIP creation)

**AMAUAT tests**: reingest-aip.feature

**External tools**: null

Given that an AIP has been stored

When the user selects "Partial re-ingest" from the AIP information page
- [ ] Then the AIP will be sent to the Ingest tab where re-ingest can be approved AND
- [ ] the microservices and jobs will follow the selected processing configuration AND
- [ ] the user can select a different normalization option than the first time (i.e. can create a DIP on demand)
- [ ] the new AIP over-writes the old one in storage
- [ ] <premis:eventType>reingestion</premis:eventType> is present in the resulting METS

### 17.13

**Sev**: High

**Current coverage in AMAUAT**: Excellent

**AMAUAT tests**: reingest-aip.feature

**External tools**: null

Given that an AIP has been stored

When the user selects "Full re-ingest" from the AIP information page
- [ ] Then the AIP will be sent to the Transfer tab where re-ingest can be approved AND
- [ ] the microservices and jobs will follow the selected processing configuration AND
- [ ] the user can select a different options than the first time (i.e. run file ID if it wasn't run the first time) AND
- [ ] the new AIP over-writes the old one in storage AND
- [ ] <premis:eventType>reingestion</premis:eventType> is present in the resulting METS AND
- [ ] any new PREMIS events are present in the resulting METS

### 17.14

**Sev**: High

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that an AIP has been stored

When the user requests deletion of the AIP from the AIP information page
- [ ] Then the status of the AIP will be "Deletion requested"
(See 24.2 for other half of the deletion test)

### 17.15

**Sev**: null

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that an encrypted storage location exists

When an AIP is stored in the encrypted storage location
- [ ] Then the AIP pointer file will include an encryption event and public key AND
- [ ] the AIP can be downloaded AND
- [ ] the AIP can be reingested and downloaded again

### 17.16

**Sev**: null

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a storage location has a replicator location connected to it

When an AIP is stored in the storage location
- [ ] Then the AIP will be saved in the storage location AND
- [ ] a second copy of the AIP will be saved in the replicator location

## 18 - Preservation Planning

### 18.1

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that the file identification command is set to Siegfried

When the user enables Fido
- [ ] Then the Siegfried command will be disabled AND
- [ ] the Fido command will be enabled AND
- [ ] when file identification runs next, Fido will be used instead of Siegfried

### 18.2

**Sev**: High

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that the user has disabled a command

When a transfer that would normally call that command is processed
- [ ] Then the command will not run AND
- [ ] the task output will not show that the command has run AND
- [ ] the METS file will not show that the command was run AND
- [ ] the command can be re-enabled later

### 18.3

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a user has edited a command

When a transfer that calls the command is processed
- [ ] Then the edited version of the command will run AND
- [ ] the task output and METS will show that the updated command ran, if applicable

### 18.4

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user has edited a command

When the user wants to revert to the previous command
- [ ] Then the user can click on "Revision history" AND
- [ ] the user can select the previous version that they would like to revert to AND
- [ ] the task output and METS will show that the reverted version of the command was run, if applicable

## 19 - Access

### 19.1

**Sev**: Low

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that some material has been uploaded to AtoM

When the user looks at the Access tab
- [ ] Then each item uploaded to AtoM should be present
- [ ] and the DIP URL should be correct- [ ]- [ ]
- [ ] and the Delete button will delete the record from the table but not the records from AtoM
(- [ ]- [ ] note: there is a known issue where /sword/deposits is being inserted in the URL)

## 20 - Administration

### 20.1

**Sev**: High

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that the user is on the Administration tab > Processing configuration

When the user selects "Edit"
- [ ] Then the processing configuration form will open AND
- [ ] the user will be able to make changes AND
- [ ] the user can save the form

### 20.2

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the user has changed some values in the default processing configuration

When a transfer is started from the dashboard
- [ ] Then the transfer should follow the decisions as set in the default processing configuration

### 20.3

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that the user is on the Administration tab > Processing configuration

When the user selects "Download"
- [ ] Then an XML file containing the processing configuration decisions set in the config form will be downloaded

### 20.4

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that the user has changed some values in the default processing configuration

When the user selects "Reset"
- [ ] Then the configuration will be reset to the standard Archivematica pre-sets (see docs for pre-set info https://www.archivematica.org/en/docs/latest/user-manual/administer/dashboard-admin/#processing-config-fields)

### 20.5

**Sev**: Medium

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that the user is on the Administration tab > Processing configuration

When the user selects "Add"
- [ ] Then a processing configuration form will open AND
- [ ] the user can select decision points AND
- [ ] the user can save the form

### 20.6

**Sev**: Low

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a custom processing configuration has been created

When the user selects "Delete" for the custom processing configuration
- [ ] Then the custom processing configuration will be deleted

### 20.7

**Sev**: null

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that the user is on the Administration tab > Storage locations

When the user increases or decreases the amount of material in a given storage location
- [ ] Then the Used storage value will increase or decrease correspondingly

### 20.8

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the user is on the Administration tab > Processing storage usage

When the user selects "Calculate disk usage”
- [ ] Then the disk usage will be calculated and displayed

### 20.9

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the user is on the Administration tab > Processing storage usage and has calculated disk usage

When the user selects "Clear" for one of the storage locations
- [ ] Then the user will be prompted to confirm the choice AND
- [ ] the folder will be cleared AND
- [ ] the usage will reset to 4.0KB

### 20.1

**Sev**: High

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that the credentials have been added to the DIP Upload page for an AtoM, Binder, or ArchivesSpace instance

When the user uploads a DIP to those systems
- [ ] Then DIP upload will be successful

### 20.11

**Sev**: High

**Current coverage in AMAUAT**: Excellent

**AMAUAT tests**: null

**External tools**: null

Given that the PREMIS agent identifier value, name, and type have been set

When the user creates an AIP
- [ ] Then the agent identifier value, name, and type are properly recorded in the METS

### 20.12

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that the user has changed a language in Administration > Languages

When the user views the dashboard
- [ ] Then the microservice tasks and interface items should appear in that language (translation completeness permitting)

### 20.13

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When the user checks the version on Administration > Version
- [ ] Then the version number should be correct AND
- [ ] the Agent code should correspond with the version

## 21 - Users & Permissions

### 21.1

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user is an administrator

When the user goes to Administration > Users
- [ ] Then the user will be able to add a new user, edit an existing user, or delete a user


### 21.2

**Sev**: High

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a user is not an administrator

When the user goes to the Administration tab
- [ ] Then the user will not see the Users menu item

### 21.3

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When LDAP is configured
null

### 21.4

**Sev**: null

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

When CAS is configured

- [ ] Then attempting to access Archivematica in the browser when not yet authenticated redirects the user to a CAS server for authentication AND
- [ ] After successfully authenticating on the CAS server, the user is logged into Archivematica AND
- [ ] A new user account is created for the user if one did not already exist AND
- [ ] Logging out from Archivematica ends the Archivematica session and logs the user out on the CAS server

## 22 - Failure Reports & Notifications

### 22.1

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a transfer has failed

When the user views Administration > Failures
- [ ] Then the user will see a failure report AND
- [ ] the user can click on the report to see which job failed AND
- [ ] the user can delete the failure report

### 22.2

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that a user has a valid email address

When a transfer fails
- [ ] Then the user will receive an emailed version of the failure report

## 23 - System Config Options

### 23.1

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that indexing has been disabled for a pipeline

When the user opens the dashboard
- [ ] Then the Backlog, Appraisal, and Archival storage tabs are not visible
- [ ] the Index AIP job will not run (? need to confirm)

### 23.2

**Sev**: Low

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that task output capturing has been disabled for the pipeline

When the user views the task ouptut page for a job that normally has some output in the standard out and standard error streams (i.e. characterize and extract metadata)
- [ ] Then there will be no data in the standard output stream AND
- [ ] There will only be data in the standard error stream if the task has returned a non-zero exit code (i.e. it failed)

## 24 - Storage Service

### 24.1

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that Fixity has been configured

When the user views the Packages tab of the Storage Service
- [ ] Then the user will see data in the Fixity Date and Fixity Status columns AND
- [ ] The information in those columns will be correct

### 24.2

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

Given that there is a DIP in storage

When the user deletes the DIP from the Packages tab
- [ ] Then the DIP will be deleted successfully

### 24.3

**Sev**: Medium

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: null

AIP Recovery
null

### 24.4

**Sev**: High

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a user has requested that an AIP be deleted using the Delete interface in the dashboard

When a Storage Service admin approves the Deletion requests in the Storage Service
- [ ] Then the AIP will be deleted AND
- [ ] the entry for the AIP will be removed from the Archival Storage tab in the dashboard AND
- [ ] a record of the decision will appear in the Closed requests table

### 24.5

**Sev**: High

**Current coverage in AMAUAT**: null

**AMAUAT tests**: null

**External tools**: null

Given that a user has requested that an AIP be deleted using the Delete interface in the dashboard

When a Storage Service admin rejects the Deletion requests in the Storage Service
- [ ] Then the AIP will not be deleted AND
- [ ] the AIP's status the Archival Storage tab in the dashboard will be set back to Stored AND
- [ ] a record of the decision will appear in the Closed requests table

## 25 - METS Validation

### 25.1

**Sev**: High

**Current coverage in AMAUAT**: None

**AMAUAT tests**: null

**External tools**: METS-RW

Given that an AIP METS file has been created

When the user validates the METS file against the PREMIS in METS Toolbox validator (http://pim.fcla.edu/validate) or against another online validator such as https://www.freeformatter.com/xml-validator-xsd.html
- [ ] Then no errors are reported AND
- [ ] The validation is successful

### 25.2

**Sev**: High

**Current coverage in AMAUAT**: Ok / Implicit (test does not specify all METS/PREMIS sections)

**AMAUAT tests**: transfer-microservices.feature

**External tools**: METS-RW

Given that an AIP METS file has been created

When the user validates the METS file against the Archivematica METS profile (created by Evelyn, not hosted anywhere yet...)
- [ ] Then the expected METS and PREMIS sections are present and they match expected values.
