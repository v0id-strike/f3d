
.. _program_listing_file_module_vtkF3DFaceVaryingPointDispatcher.h:

Program Listing for File vtkF3DFaceVaryingPointDispatcher.h
===========================================================

|exhale_lsh| :ref:`Return to documentation for file <file_module_vtkF3DFaceVaryingPointDispatcher.h>` (``module/vtkF3DFaceVaryingPointDispatcher.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   #ifndef vtkF3DFaceVaryingPointDispatcher_h
   #define vtkF3DFaceVaryingPointDispatcher_h
   
   #include <vtkPolyDataAlgorithm.h>
   
   #include "vtkextModule.h"
   
   class VTKEXT_EXPORT vtkF3DFaceVaryingPointDispatcher : public vtkPolyDataAlgorithm
   {
   public:
     static vtkF3DFaceVaryingPointDispatcher* New();
     vtkTypeMacro(vtkF3DFaceVaryingPointDispatcher, vtkPolyDataAlgorithm);
   
     static vtkInformationIntegerKey* INTERPOLATION_TYPE();
   
   protected:
     vtkF3DFaceVaryingPointDispatcher();
     ~vtkF3DFaceVaryingPointDispatcher() override;
   
     int RequestData(vtkInformation*, vtkInformationVector**, vtkInformationVector*) override;
   
   private:
     vtkF3DFaceVaryingPointDispatcher(const vtkF3DFaceVaryingPointDispatcher&) = delete;
     void operator=(const vtkF3DFaceVaryingPointDispatcher&) = delete;
   };
   
   #endif
