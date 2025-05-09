# PHP Imagick tasks

## Source issues

- **Bug**: CI build issue for ImageMagick-6.7.8-0
  - https://github.com/Imagick/imagick/issues/734 - ImageMagick-6.7.8-0 librsvg compilation issues
- **Bug**: Investigate parse error for `php -ri imagick`
  - https://github.com/Imagick/imagick/issues/694 - php -ri imagick fails with error
- **Bug**: Look into cleaning up temp files when FPM kill the process (more for policy options)
  - https://github.com/Imagick/imagick/issues/681 - Leaking temp files in PHP-FPM when max_execution_time interrupts the script
- **Bug**: Look into backtick issue in the ImageMagick policy
  - https://github.com/Imagick/imagick/issues/670 - Backticks in XML Comment breaks policy in /etc/ImageMagick-6/policy.xml
- **Bug**: Investigate perf regression between PHP 7.2 and 8.2 when using distort
  - https://github.com/Imagick/imagick/issues/731 - Performance Regression with Imagick between PHP 7.2 and 8.2
- **Bug**: Fix reference leaks in subimageMatch and possibly elsewhere
  - https://github.com/Imagick/imagick/issues/725 - References can cause leaks
- **Bug**: Look into unexpected ignoring of blur parameter
  - https://github.com/Imagick/imagick/issues/680 - Imagick::resize doesn't use the filter parameter...
- **Bug**: Look into shadowImage params effect
  - https://github.com/Imagick/imagick/issues/686 - shadowImage() Coordinates Have no Effect
- **Bug**: Look into shadow webp issue
  - https://github.com/Imagick/imagick/issues/665 - Shadow-like line&row compression artefacts when saving to webp
- **Bug**: Check why compression quality is ignored for HEIC / AVIC
  - https://github.com/Imagick/imagick/issues/711 - AVIF/HEIC compression quality settings have no effect on output file size
  - https://github.com/Imagick/imagick/issues/696 - Highest compression for AVIF images and google pagespeed
- **Bug**: Check why output from getImagesBlob is empty for HEIC
  - https://github.com/Imagick/imagick/issues/707 - Empty HEIC-encoding result with Ubuntu 24.04
- **Bug**: Look into incorrect usage of preview image in NEF images
  - https://github.com/Imagick/imagick/issues/685 - PHP Imagick::readImageFile NEF filehandle detected as TIFF
- **Bug**: Look into ImageMagick update from v6 to v7 image negate related issue
  - https://github.com/Imagick/imagick/issues/676 - Imagick v6 to v7 upgrade
- **Bug**: Investigate what could cause error in RenderMVGContent
  - https://github.com/Imagick/imagick/issues/703 - Non-conforming drawing primitive definition `9' @ error/draw.c/RenderMVGContent/4414
- **Bug**: OMP - Investigate segfault in furier tranform image
  - https://github.com/Imagick/imagick/issues/724 - erratic segfault on tests/151_Imagick_subImageMatch_basic.phpt
- **Bug**: Check support for RTL languagues not working on Ubuntu
  - https://github.com/Imagick/imagick/issues/712 - Long standing problem with RTL languages
- **Bug**: Look into options for procession SVG
  - https://github.com/Imagick/imagick/issues/706 - does not support transform attributes which contain more than one transform
- **Bug**: Look what imagick SVG does not work on Google App Engine
  - https://github.com/Imagick/imagick/issues/687 - Imagick not working with GAE runtime php82 or php83
- **Bug**: Win - Try Ghostscript generation
  - https://github.com/Imagick/imagick/issues/713 - Ghostscript call by imagick doesn't work


## Feedback required

- **Feat**: config path
  - https://github.com/Imagick/imagick/issues/736 - [Feature Request] Config directive to set path


## Tasks

- Blog post about PHP Foundation support
  - https://github.com/Imagick/imagick/issues/718 - New Maintainers introduction? 