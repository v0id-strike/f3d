
.. _program_listing_file_module_vtkF3DBitonicSort.h:

Program Listing for File vtkF3DBitonicSort.h
============================================

|exhale_lsh| :ref:`Return to documentation for file <file_module_vtkF3DBitonicSort.h>` (``module/vtkF3DBitonicSort.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   
   #ifndef vtkF3DBitonicSort_h
   #define vtkF3DBitonicSort_h
   
   #include <vtkNew.h>
   #include <vtkObject.h>
   
   #include "vtkextModule.h"
   
   class vtkShader;
   class vtkShaderProgram;
   class vtkOpenGLBufferObject;
   class vtkOpenGLRenderWindow;
   
   class VTKEXT_EXPORT vtkF3DBitonicSort : public vtkObject
   {
   public:
     static vtkF3DBitonicSort* New();
     vtkTypeMacro(vtkF3DBitonicSort, vtkObject);
   
     bool Initialize(int workgroupSize, int keyType, int valueType);
   
     bool Run(vtkOpenGLRenderWindow* context, int nbPairs, vtkOpenGLBufferObject* keys,
       vtkOpenGLBufferObject* values);
   
   private:
     vtkNew<vtkShader> BitonicSortLocalSortComputeShader;
     vtkNew<vtkShaderProgram> BitonicSortLocalSortProgram;
     vtkNew<vtkShader> BitonicSortLocalDisperseComputeShader;
     vtkNew<vtkShaderProgram> BitonicSortLocalDisperseProgram;
     vtkNew<vtkShader> BitonicSortGlobalFlipComputeShader;
     vtkNew<vtkShaderProgram> BitonicSortGlobalFlipProgram;
     vtkNew<vtkShader> BitonicSortGlobalDisperseComputeShader;
     vtkNew<vtkShaderProgram> BitonicSortGlobalDisperseProgram;
   
     int WorkgroupSize = -1;
   };
   
   #endif
