
.. _program_listing_file_module_F3DUtils.cxx:

Program Listing for File F3DUtils.cxx
=====================================

|exhale_lsh| :ref:`Return to documentation for file <file_module_F3DUtils.cxx>` (``module/F3DUtils.cxx``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   #include "F3DUtils.h"
   
   #include <vtkObject.h>
   #include <vtkSetGet.h>
   
   #include <stdexcept>
   
   //----------------------------------------------------------------------------
   double F3DUtils::ParseToDouble(const std::string& str, double def, const std::string& nameError)
   {
     double value = def;
     if (!str.empty())
     {
       try
       {
         value = std::stod(str);
       }
       catch (const std::invalid_argument&)
       {
         vtkWarningWithObjectMacro(
           nullptr, "Could not parse " << nameError << ": " << str << ". Ignoring.");
       }
       catch (const std::out_of_range&)
       {
         vtkWarningWithObjectMacro(
           nullptr, "Provided " << nameError << " out of range: " << str << ". Ignoring.");
       }
     }
     return value;
   }
