#
# Bareflank Hypervisor
# Copyright (C) 2015 Assured Information Security, Inc.
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301 USA

include(${CMAKE_INSTALL_PREFIX}/cmake/CMakeGlobal_Includes.txt)

# ------------------------------------------------------------------------------
# Targets
# ------------------------------------------------------------------------------

add_library(test_support STATIC test_real_elf.cpp test_fake_elf.cpp)

macro(do_test str)
    add_executable(test_${str} test_${str}.cpp)
    target_link_libraries(test_${str} test_support)
    target_link_libraries(test_${str} test_catch)
    add_test(bfelf_${str} test_${str})
endmacro(do_test)

do_test(binary)
do_test(file_get_entry)
do_test(file_get_load_instr)
do_test(file_get_needed)
do_test(file_get_needed_list)
do_test(file_get_num_load_instrs)
do_test(file_get_num_needed)
do_test(file_get_pic_pie)
do_test(file_get_relro)
do_test(file_get_section_info)
do_test(file_get_stack_perm)
do_test(file_get_total_size)
do_test(file_init)
do_test(helpers)
do_test(load)
do_test(loader_add)
do_test(loader_relocate)
do_test(loader_resolve_symbol)
do_test(read_binary_and_get_needed_list)
do_test(real)
do_test(set_args)
do_test(set_integer_args)