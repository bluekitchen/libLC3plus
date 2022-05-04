cmake_minimum_required(VERSION 3.9)

project(lc3plus_fixedpoint
	    VERSION 1.3.6
	    DESCRIPTION "LC3plus fixedpoint library"
	    HOMEPAGE_URL "https://www.iis.fraunhofer.de/en/ff/amm/communication/lc3.html"
	    LANGUAGES C)

add_definitions(-DWMOPS=0 -DDONT_COUNT_MEM)

add_library(LC3plus SHARED
    adjust_global_gain_fx.c
    al_fec.c
    apply_global_gain_fx.c
    ari_codec.c
    attack_detector_fx.c
    basop_mpy.c
    basop_util.c
    constants.c
    cutoff_bandwidth.c
    dct2_fx.c
    dct4_fx.c
    dec_entropy.c
    dec_lc3.c
    detect_cutoff_warped_fx.c
    enc_entropy.c
    enc_lc3.c
    estimate_global_gain_fx.c
    fft.c
    imdct_fx.c
    lc3.c
    levinson_fx.c
    ltpf_coder_fx.c
    ltpf_decoder_fx.c
    mdct_fx.c
    mdct_shaping_fx.c
    near_nyquist_detector_fx.c
    noise_factor_fx.c
    noise_filling_fx.c
    olpa_fx.c
    pc_apply_fx.c
    pc_classify_fx.c
    pc_main_fx.c
    pc_update_fx.c
    per_band_energy_fx.c
    plc_apply_fx.c
    plc_classify_fx.c
    plc_damping_scrambling_fx.c
    plc_lpc_scaling_fx.c
    plc_main_fx.c
    plc_noise_substitution_fx.c
    plc_phecu_f0_refine_first_fx.c
    plc_phecu_fec_hq_fx.c
    plc_phecu_lf_peak_analysis_fx.c
    plc_phecu_peak_locator_fx.c
    plc_phecu_setf0hz_fx.c
    plc_phecu_tools_fx.c
    plc_tdac_fx.c
    plc_tdc_inverse_odft_fx.c
    plc_tdc_lagwin_fx.c
    plc_tdc_main_fx.c
    plc_tdc_pre_emphasis_fx.c
    plc_update_aft_imdct_fx.c
    plc_update_fx.c
    plc_xcorr_fx.c
    pvq_dec_fx.c
    pvq_enc_fx.c
    pvq_index_fx.c
    quantize_spec_fx.c
    reorder_bitstream_fx.c
    resamp12k8_fx.c
    residual_coding_fx.c
    residual_decoding_fx.c
    rom_basop_util.c
    scale_signal24_fx.c
    setup_dec_lc3.c
    setup_enc_lc3.c
    sns_compute_scf_fx.c
    sns_interpolate_scf_fx.c
    sns_quantize_scf_fx.c
    tns_coder_fx.c
    tns_decoder_fx.c
    basic_op/basop32.c
    basic_op/control.c
    basic_op/count.c
    basic_op/dynmem.c
    basic_op/enh1632.c
    basic_op/enh40.c
    basic_op/enhUL32.c
)

include_directories(basic_op)

SET(CMAKE_C_FLAGS  "${CMAKE_C_FLAGS} -pedantic -Wcast-qual -Wall -W -Wextra -Wno-long-long")
SET(CMAKE_C_FLAGS  "${CMAKE_C_FLAGS} -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes")
SET(CMAKE_C_FLAGS  "${CMAKE_C_FLAGS} -Werror-implicit-function-declaration")

set_target_properties(LC3plus PROPERTIES VERSION ${PROJECT_VERSION})

set_target_properties(LC3plus PROPERTIES PUBLIC_HEADER lc3.h)

target_link_libraries(LC3plus m)

include(GNUInstallDirs)

install(TARGETS LC3plus
    LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}/LC3plus
    PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}/LC3plus)

configure_file(LC3plus.pc.in LC3plus.pc @ONLY)

install(FILES ${CMAKE_BINARY_DIR}/LC3plus.pc DESTINATION ${CMAKE_INSTALL_DATAROOTDIR}/pkgconfig)
