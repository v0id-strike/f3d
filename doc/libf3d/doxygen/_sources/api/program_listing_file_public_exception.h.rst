
.. _program_listing_file_public_exception.h:

Program Listing for File exception.h
====================================

|exhale_lsh| :ref:`Return to documentation for file <file_public_exception.h>` (``public/exception.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   #ifndef f3d_exception_h
   #define f3d_exception_h
   
   #include <stdexcept>
   #include <string>
   
   namespace f3d
   {
   struct exception : public std::runtime_error
   {
     explicit exception(const std::string& what = "")
       : std::runtime_error(what)
     {
     }
   };
   }
   
   #endif
