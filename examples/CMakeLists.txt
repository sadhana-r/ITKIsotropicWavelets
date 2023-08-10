cmake_minimum_required(VERSION 3.5)
project(IsotropicWaveletsExamples)

if(NOT ITK_SOURCE_DIR)
  find_package(ITK 5 REQUIRED COMPONENTS IsotropicWavelets ITKCommon ITKImageGrid ITKImageIntensity ITKImageStatistics ITKImageIO)
else()
  # when being built as part of ITK, ITKImageIO and ITKTransformIO
  # lists of modules are not yet ready, causing a configure error
  find_package(ITK REQUIRED COMPONENTS IsotropicWavelets ITKCommon ITKImageGrid ITKImageIntensity ITKImageStatistics ITKIOImageBase ITKIONRRD)
endif()

include(${ITK_USE_FILE})
include_directories(SYSTEM ${ITK_INCLUDE_DIRS})

add_executable(runWaveletCoeffsSpatialDomainImageFilter_example runWaveletCoeffsSpatialDomainImageFilter_example.cxx)
target_link_libraries(runWaveletCoeffsSpatialDomainImageFilter_example PUBLIC ${ITK_LIBRARIES})

add_executable(runWaveletCoeffsPhaseAnalyzisImageFilter_example runWaveletCoeffsPhaseAnalyzisImageFilter_example.cxx)
target_link_libraries(runWaveletCoeffsPhaseAnalyzisImageFilter_example PUBLIC ${ITK_LIBRARIES})

add_executable(runRieszWaveletAnalysis runRieszWaveletAnalysis.cpp)
target_link_libraries(runRieszWaveletAnalysis PUBLIC ${ITK_LIBRARIES})
