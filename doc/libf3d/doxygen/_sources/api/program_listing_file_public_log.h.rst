
.. _program_listing_file_public_log.h:

Program Listing for File log.h
==============================

|exhale_lsh| :ref:`Return to documentation for file <file_public_log.h>` (``public/log.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   #ifndef f3d_log_h
   #define f3d_log_h
   
   #include "export.h"
   
   #include <sstream>
   #include <string>
   
   namespace f3d
   {
   class F3D_EXPORT log
   {
   public:
     enum class VerboseLevel : unsigned char
     {
       DEBUG = 0,
       INFO,
       WARN,
       ERROR,
       QUIET
     };
   
     template<typename... Args>
     static void print(VerboseLevel level, Args... args)
     {
       std::stringstream ss;
       log::appendArg(ss, args...);
       log::printInternal(level, ss.str());
     }
   
     template<typename... Args>
     static void debug(Args... args)
     {
       std::stringstream ss;
       log::appendArg(ss, args...);
       log::debugInternal(ss.str());
     }
   
     template<typename... Args>
     static void info(Args... args)
     {
       std::stringstream ss;
       log::appendArg(ss, args...);
       log::infoInternal(ss.str());
     }
   
     template<typename... Args>
     static void warn(Args... args)
     {
       std::stringstream ss;
       log::appendArg(ss, args...);
       log::warnInternal(ss.str());
     }
   
     template<typename... Args>
     static void error(Args... args)
     {
       std::stringstream ss;
       log::appendArg(ss, args...);
       log::errorInternal(ss.str());
     }
   
     static void setUseColoring(bool use);
   
     static void setVerboseLevel(VerboseLevel level, bool forceStdErr = false);
   
   protected:
     static void appendArg(std::stringstream&)
     {
     }
   
     template<typename T, typename... Args>
     static void appendArg(std::stringstream& ss, T value, Args... args)
     {
       ss << value;
       log::appendArg(ss, args...);
     }
   
     static void printInternal(VerboseLevel level, const std::string& msg);
     static void errorInternal(const std::string& msg);
     static void warnInternal(const std::string& msg);
     static void infoInternal(const std::string& msg);
     static void debugInternal(const std::string& msg);
   };
   }
   
   #endif
