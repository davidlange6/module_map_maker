Usage

Make a list of all headers you want in allt.txt. Eg

accumulators/accumulators.hpp
accumulators/accumulators_fwd.hpp
accumulators/framework/accumulator_base.hpp
accumulators/framework/accumulator_concept.hpp

The hack build_pcm to have the flags you need for boost

BOOST_FLAGS="-DBOOST_SPIRIT_THREADSAFE -DPHOENIX_THREADSAFE -DBOOST_MATH_DISABLE_STD_FPCLASSIFY -DBOOST_UUID_RANDOM_PROVIDER_FORCE_POSIX -I${BOOST_ROOT}/include/ -I${BOOST_ROOT}/include/boost -I${FFTW3_ROOT}/include -I${PYTHON3_ROOT}/include/python3.9"

rootcling dummy_dict.cc -v3 $flags -moduleMapFile=${mm_loc} -s ./libDummy.so -moduleMapFile=dummy.modulemap -cxxmodule -m ${mod} -mByproduct ${mod}  -I${mm_dir}/.. empty.h $BOOST_FLAGS 

Then run

./module_map_maker -p boost -i allt.txt -t boost -m /dlange/230125/el8_amd64_gcc11/external/boost/1.80.0-527200c4c09defc8b31ed85c4066bcdf/include/boost/module.modulemap
