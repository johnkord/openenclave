# Copyright (c) Microsoft Corporation. All rights reserved.
# Licensed under the MIT License.

##==============================================================================
##
## These rules generate the edge routines for the internal SGX-specific
## ECALLs/OCALLs used by liboehost/liboecore.
##
##==============================================================================


set(SGX_EDL_FILE ${EDL_DIR}/sgx/sgx.edl)

add_custom_command(
    OUTPUT sgx_u.h sgx_u.c sgx_args.h
    DEPENDS ${SGX_EDL_FILE} edger8r
    COMMAND edger8r --search-path ${EDL_DIR} --untrusted ${SGX_EDL_FILE})

add_custom_target(sgx_untrusted_edl
    DEPENDS sgx_u.h sgx_u.c sgx_args.h)