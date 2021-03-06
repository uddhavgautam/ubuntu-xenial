#
# Makefile for the drm device driver.  This driver provides support for the
# Direct Rendering Infrastructure (DRI) in XFree86 4.1.0 and higher.

ccflags-y := -Iinclude/drm -Idrivers/gpu/drm/amd/include/asic_reg \
	-Idrivers/gpu/drm/amd/include \
	-Idrivers/gpu/drm/amd/amdgpu \
	-Idrivers/gpu/drm/amd/scheduler

amdgpu-y := amdgpu_drv.o

# add KMS driver
amdgpu-y += amdgpu_device.o amdgpu_kms.o \
	amdgpu_atombios.o atombios_crtc.o amdgpu_connectors.o \
	atom.o amdgpu_fence.o amdgpu_ttm.o amdgpu_object.o amdgpu_gart.o \
	amdgpu_encoders.o amdgpu_display.o amdgpu_i2c.o \
	amdgpu_fb.o amdgpu_gem.o amdgpu_ring.o \
	amdgpu_cs.o amdgpu_bios.o amdgpu_benchmark.o amdgpu_test.o \
	amdgpu_pm.o atombios_dp.o amdgpu_afmt.o amdgpu_trace_points.o \
	atombios_encoders.o amdgpu_semaphore.o amdgpu_sa.o atombios_i2c.o \
	amdgpu_prime.o amdgpu_vm.o amdgpu_ib.o amdgpu_pll.o \
	amdgpu_ucode.o amdgpu_bo_list.o amdgpu_ctx.o amdgpu_sync.o

# add asic specific block
amdgpu-$(CONFIG_DRM_AMDGPU_CIK)+= cik.o gmc_v7_0.o cik_ih.o kv_smc.o kv_dpm.o \
	ci_smc.o ci_dpm.o dce_v8_0.o gfx_v7_0.o cik_sdma.o uvd_v4_2.o vce_v2_0.o \
	amdgpu_amdkfd_gfx_v7.o

amdgpu-y += \
	vi.o

# add GMC block
amdgpu-y += \
	gmc_v8_0.o

# add IH block
amdgpu-y += \
	amdgpu_irq.o \
	amdgpu_ih.o \
	iceland_ih.o \
	tonga_ih.o \
	cz_ih.o

# add SMC block
amdgpu-y += \
	amdgpu_dpm.o \
	cz_smc.o cz_dpm.o \
	tonga_smc.o tonga_dpm.o \
	fiji_smc.o fiji_dpm.o \
	iceland_smc.o iceland_dpm.o

# add DCE block
amdgpu-y += \
	dce_v10_0.o \
	dce_v11_0.o

# add GFX block
amdgpu-y += \
	amdgpu_gfx.o \
	gfx_v8_0.o

# add async DMA block
amdgpu-y += \
	sdma_v2_4.o \
	sdma_v3_0.o

# add UVD block
amdgpu-y += \
	amdgpu_uvd.o \
	uvd_v5_0.o \
	uvd_v6_0.o

# add VCE block
amdgpu-y += \
	amdgpu_vce.o \
	vce_v3_0.o

# add amdkfd interfaces
amdgpu-y += \
	 amdgpu_amdkfd.o \
	 amdgpu_amdkfd_gfx_v8.o

# add cgs
amdgpu-y += amdgpu_cgs.o

# GPU scheduler
amdgpu-y += \
	../scheduler/gpu_scheduler.o \
	../scheduler/sched_fence.o \
	amdgpu_sched.o

amdgpu-$(CONFIG_COMPAT) += amdgpu_ioc32.o
amdgpu-$(CONFIG_VGA_SWITCHEROO) += amdgpu_atpx_handler.o
amdgpu-$(CONFIG_ACPI) += amdgpu_acpi.o
amdgpu-$(CONFIG_MMU_NOTIFIER) += amdgpu_mn.o

obj-$(CONFIG_DRM_AMDGPU)+= amdgpu.o

CFLAGS_amdgpu_trace_points.o := -I$(src)
