cmake_minimum_required(VERSION 3.16)

Project(join)

find_package(Boost REQUIRED COMPONENTS thread system)
find_package(ENCRYPTO_utils REQUIRED)
find_package(OTExtension REQUIRED)
find_package(ABY REQUIRED)

add_executable(join
	join.cpp
	nest_loop_join.cpp
	hash_join.cpp
	sort_merge_join.cpp
	utils.cpp
	obliv_permutation.cpp
	fast_join.cpp
	obliv_join.cpp
	murmur_hash3.cpp
	)

add_executable(test
	test.cpp
	utils.cpp
	obliv_permutation.cpp
)

target_link_libraries(join PUBLIC
	ABY::aby
	relic_s
)

target_include_directories(join PUBLIC
	${ENCRYPTO_utils_INCLUDE_DIRS}
	${OTExtension_INCLUDE_DIRS}
	${ABY_INCLUDE_DIRS}
)

target_link_libraries(test PUBLIC
	ABY::aby
	relic_s
)

target_include_directories(test PUBLIC
	${ENCRYPTO_utils_INCLUDE_DIRS}
	${OTExtension_INCLUDE_DIRS}
	${ABY_INCLUDE_DIRS}
)
