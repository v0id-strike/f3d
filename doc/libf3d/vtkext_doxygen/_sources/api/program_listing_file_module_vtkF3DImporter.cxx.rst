
.. _program_listing_file_module_vtkF3DImporter.cxx:

Program Listing for File vtkF3DImporter.cxx
===========================================

|exhale_lsh| :ref:`Return to documentation for file <file_module_vtkF3DImporter.cxx>` (``module/vtkF3DImporter.cxx``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   #include "vtkF3DImporter.h"
   
   #include <vtkInformationIntegerKey.h>
   
   vtkInformationKeyMacro(vtkF3DImporter, ACTOR_IS_ARMATURE, Integer);
   
   #if VTK_VERSION_NUMBER >= VTK_VERSION_CHECK(9, 3, 20240707)
   
   //----------------------------------------------------------------------------
   bool vtkF3DImporter::UpdateAtTimeValue(double vtkNotUsed(timeValue))
   {
     return this->GetUpdateStatus() == vtkImporter::UpdateStatusEnum::SUCCESS;
   }
   
   #else
   
   //----------------------------------------------------------------------------
   bool vtkF3DImporter::UpdateAtTimeValue(double vtkNotUsed(timeValue))
   {
     return true;
   }
   
   //----------------------------------------------------------------------------
   void vtkF3DImporter::UpdateTimeStep(double timeValue)
   {
     this->UpdateAtTimeValue(timeValue);
   }
   
   #endif
   
   //----------------------------------------------------------------------------
   void vtkF3DImporter::SetFailureStatus()
   {
   #if VTK_VERSION_NUMBER >= VTK_VERSION_CHECK(9, 3, 20240707)
     this->SetUpdateStatus(vtkImporter::UpdateStatusEnum::FAILURE);
   #endif
   }
