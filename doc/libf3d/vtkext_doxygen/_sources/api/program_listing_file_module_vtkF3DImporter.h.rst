
.. _program_listing_file_module_vtkF3DImporter.h:

Program Listing for File vtkF3DImporter.h
=========================================

|exhale_lsh| :ref:`Return to documentation for file <file_module_vtkF3DImporter.h>` (``module/vtkF3DImporter.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   #ifndef vtkF3DImporter_h
   #define vtkF3DImporter_h
   
   #include "vtkextModule.h"
   
   #include <vtkImporter.h>
   #include <vtkVersion.h>
   
   class vtkInformationIntegerKey;
   
   class VTKEXT_EXPORT vtkF3DImporter : public vtkImporter
   {
   public:
     static vtkInformationIntegerKey* ACTOR_IS_ARMATURE();
   
   #if VTK_VERSION_NUMBER >= VTK_VERSION_CHECK(9, 3, 20240707)
     bool UpdateAtTimeValue(double timeValue) override;
   #else
     virtual bool UpdateAtTimeValue(double timeValue);
     void UpdateTimeStep(double timeValue) override;
   #endif
   
     void SetFailureStatus();
   };
   
   #endif
