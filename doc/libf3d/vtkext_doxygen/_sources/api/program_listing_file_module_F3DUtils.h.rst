
.. _program_listing_file_module_F3DUtils.h:

Program Listing for File F3DUtils.h
===================================

|exhale_lsh| :ref:`Return to documentation for file <file_module_F3DUtils.h>` (``module/F3DUtils.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   #ifndef F3DUtils_h
   #define F3DUtils_h
   
   #include "vtkextModule.h"
   
   #include <string>
   
   namespace F3DUtils
   {
   /*
    * Convert provided std into a double and returns it.
    * Catch conversion error, log them if any and returns the provided def value.
    * Use nameError in the log for easier debugging.
    */
   VTKEXT_EXPORT double ParseToDouble(
     const std::string& str, double def, const std::string& nameError);
   };
   
   #endif
