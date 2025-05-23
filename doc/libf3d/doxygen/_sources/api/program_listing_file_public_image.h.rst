
.. _program_listing_file_public_image.h:

Program Listing for File image.h
================================

|exhale_lsh| :ref:`Return to documentation for file <file_public_image.h>` (``public/image.h``)

.. |exhale_lsh| unicode:: U+021B0 .. UPWARDS ARROW WITH TIP LEFTWARDS

.. code-block:: cpp

   #ifndef f3d_image_h
   #define f3d_image_h
   
   #include "exception.h"
   #include "export.h"
   
   #include <filesystem>
   #include <string>
   #include <vector>
   
   namespace f3d
   {
   class F3D_EXPORT image
   {
   public:
     enum class SaveFormat : unsigned char
     {
       PNG,
       JPG,
       TIF,
       BMP
     };
   
     enum class ChannelType : unsigned char
     {
       BYTE,
       SHORT,
       FLOAT
     };
   
     explicit image(const std::filesystem::path& filePath);
   
     image(unsigned int width, unsigned int height, unsigned int channelCount,
       ChannelType type = ChannelType::BYTE);
   
   
     image();
     ~image();
     image(const image& img);
     image& operator=(const image& img) noexcept;
     image(image&& img) noexcept;
     image& operator=(image&& img) noexcept;
   
   
     [[nodiscard]] bool operator==(const image& reference) const;
     [[nodiscard]] bool operator!=(const image& reference) const;
   
     [[nodiscard]] std::vector<double> getNormalizedPixel(const std::pair<int, int>& xy) const;
   
     [[nodiscard]] static std::vector<std::string> getSupportedFormats();
   
   
     [[nodiscard]] unsigned int getWidth() const;
     [[nodiscard]] unsigned int getHeight() const;
   
   
     [[nodiscard]] unsigned int getChannelCount() const;
   
     [[nodiscard]] ChannelType getChannelType() const;
   
     [[nodiscard]] unsigned int getChannelTypeSize() const;
   
   
     image& setContent(void* buffer);
     [[nodiscard]] void* getContent() const;
   
     double compare(const image& reference) const;
   
     const image& save(
       const std::filesystem::path& filePath, SaveFormat format = SaveFormat::PNG) const;
   
     [[nodiscard]] std::vector<unsigned char> saveBuffer(SaveFormat format = SaveFormat::PNG) const;
   
     const image& toTerminalText(std::ostream& stream) const;
   
     [[nodiscard]] std::string toTerminalText() const;
   
     f3d::image& setMetadata(std::string key, std::string value);
   
     [[nodiscard]] std::string getMetadata(const std::string& key) const;
   
     [[nodiscard]] std::vector<std::string> allMetadata() const;
   
     struct write_exception : public exception
     {
       explicit write_exception(const std::string& what = "");
     };
   
     struct read_exception : public exception
     {
       explicit read_exception(const std::string& what = "");
     };
   
     struct metadata_exception : public exception
     {
       explicit metadata_exception(const std::string& what = "");
     };
   
   private:
     class internals;
     internals* Internals;
   };
   }
   
   #endif
