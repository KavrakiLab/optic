find_package(Clp)
find_package(CoinUtils)
find_package(Cbc)
find_package(Cgl)
find_package(OSI)
find_package(GSL)

include_directories(${val_SOURCE_DIR} ${val_SOURCE_DIR}/parsing ${CLP_INCLUDES}/coin ${CBC_INCLUDES}/coin ${CPLEX_INCLUDES} ${CONCERT_INCLUDES}  ${GSL_INCLUDES})

set(optic_build_srcs
    compressionsafescheduler.cpp
    totalordertransformer.cpp
    partialordertransformer.cpp
    FFSolver.cpp
    FFEvent.cpp
    globals.cpp
    lpscheduler.cpp
    RPGBuilder.cpp
    RPGBuilderAnalysis.cpp
    RPGBuilderEvaluation.cpp
    RPGBuilderNumerics.cpp
    temporalanalysis.cpp
    minimalstate.cpp
    temporalconstraints.cpp
    numericanalysis.cpp
    solver.cpp
    NNF.cpp
    PreferenceHandler.cpp
    choosepreconditions.cpp)

add_library(OpticCommon STATIC ${optic_build_srcs})
target_link_libraries(OpticCommon ParsePDDL Inst)
SET_TARGET_PROPERTIES(OpticCommon PROPERTIES COMPILE_FLAGS "-DPOPF3ANALYSIS")

ADD_EXECUTABLE(optic-clp opticMain.cpp solver-clp.cpp)
target_link_libraries(optic-clp
    OpticCommon
    ${CBC_SOLVER_LIBRARY} ${CBC_LIBRARY} ${CGL_LIBRARIES} ${OSICLP_LIBRARIES} ${OSI_LIBRARIES} ${CLP_LIBRARIES}  ${COINUTILS_LIBRARIES} -lz -lbz2
    )
SET_TARGET_PROPERTIES(optic-clp PROPERTIES COMPILE_FLAGS "-DPOPF3ANALYSIS")
