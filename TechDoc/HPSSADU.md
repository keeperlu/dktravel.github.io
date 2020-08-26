Running HPSSADUCLI
------------------------------------------------------------------------
To run the command-line application:   
   Open a command prompt and change directory (cd) to the location
      where HPSSADUCLI is installed.  This is commonly
         C:\Program Files\hp\hpssaducli\bin.
   To generate a diagnostic report, enter the following command:

       hpssaducli -f adu-report.zip

   To generate a SmartSSD Wear gauge report, enter the following command:

       hpssaducli -ssdrpt -f ssd-report.zip
  
   More options can be found by "hpssaducli -help".
      
Additional Notes
----------------
Both the diagnostic and SmartSSD wear gauge reports are generated in compressed
  (ZIP) format.

The diagnostic report output archive contains the following files:

   * ADUReport.txt          => Diagnostic report in text format
   * ADUReport.xml          => Diagnostic report in XML format
   * ADUReport.htm          => HTML viewer for diagnostic report
   * report.checksum        => checksum file
   * SlotX.txt (SlotX.old)  => Controller serial output log

   Note: The serial output log file(s) are only available if the "HP Smart
         Array SAS/SATA Event Notification Service" is installed and running.

   To view the diagnostic report in a browser, extract the ADUReport.htm. Open
      ADUReport.htm in the browser.

The SmartSSD wear gauge report output archive contains the following files:

   * SmartSSDWearGaugeReport.txt  => SmartSSD wear gauge report in text format
   * SmartSSDWearGaugeReport.json => SmartSSD wear gauge report in JSON format
   * SmartSSDWearGaugeReport.htm  => HTML viewer for the JSON wear gauge report

   To view the SmartSSD wear gauge report in a browser, extract the
   SmartSSDWearGaugeReport.json, SmartSSDWearGaugeReport.htm files to a
   directory (both files must reside in the same directory).  Open
   SmartSSDWearGaugeReport.htm in the browser.

Known Issues
------------
* When installing the 32-bit version of HPSSADUCLI on a system that has a
  64-bit (x64) version of HPSSAADUCLI installed, please uninstall the 64-bit
  version first. Failing to uninstall the 64-bit version will cause the 32-bit
  installation to fail.
