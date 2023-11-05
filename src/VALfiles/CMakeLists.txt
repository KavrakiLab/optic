add_subdirectory(parsing)

include_directories(${CMAKE_CURRENT_SOURCE_DIR} ${CMAKE_CURRENT_BINARY_DIR} ${ParsePDDL_SOURCE_DIR})

set(libInst_SRCS
      SimpleEval.cpp
      FastEnvironment.cpp instantiation.cpp
      typecheck.cpp TypedAnalyser.cpp FuncAnalysis.cpp
      TIM.cpp TimSupport.cpp TypeStripWC.cpp
)

add_library(Inst STATIC ${libInst_SRCS})

set(validate_SRCS
     Action.cpp Proposition.cpp FuncExp.cpp typecheck.cpp main.cpp
     Validator.cpp RepairAdvice.cpp LaTeXSupport.cpp State.cpp Plan.cpp Ownership.cpp
     Environment.cpp Polynomial.cpp Utils.cpp
     TrajectoryConstraints.cpp RobustAnalyse.cpp random.cpp Events.cpp PrettyPrinter.cpp)
     
add_executable(validate ${validate_SRCS})

target_link_libraries(validate
        ParsePDDL
)

set(parser_SRCS
     parse.cpp
)

add_executable(parser ${parser_SRCS})

target_link_libraries(parser
        ParsePDDL
)


