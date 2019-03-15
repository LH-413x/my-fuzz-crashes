
```bash
alex@alex-pc:~/code-reviww/fuzz/libbpg-all/libbpg-0.9.8$ ./bpgdec /home/alex/code-reviww/libbpg-0.9.8/out/crashes.2019-03-15-14\:00\:00/id:000000,sig:11,src:000001,op:flip1,pos:22  -o out.png
=================================================================
==16071==ERROR: AddressSanitizer: heap-buffer-overflow on address 0x6250000000de at pc 0x0000004d75c2 bp 0x7fff1cc1b270 sp 0x7fff1cc1aa20
READ of size 4 at 0x6250000000de thread T0
    #0 0x4d75c1 in __asan_memcpy (/home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/bpgdec+0x4d75c1)
    #1 0x55c95e in restore_tqb_pixels /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libavcodec/hevc_filter.c:228:25
    #2 0x55b223 in sao_filter_CTB /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libavcodec/hevc_filter.c
    #3 0x55898e in ff_hevc_hls_filter /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libavcodec/hevc_filter.c:890:13
    #4 0x55c023 in ff_hevc_hls_filters /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libavcodec/hevc_filter.c:912:9
    #5 0x51c0ac in hls_decode_entry /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libavcodec/hevc.c:2395:9
    #6 0x548d2f in avcodec_default_execute /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libavcodec/utils.c:121:17
    #7 0x516e13 in hls_slice_data /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libavcodec/hevc.c:2413:5
    #8 0x516e13 in decode_nal_unit /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libavcodec/hevc.c:2826
    #9 0x516e13 in decode_nal_units /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libavcodec/hevc.c:3063
    #10 0x516e13 in hevc_decode_frame /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libavcodec/hevc.c:3193
    #11 0x5498ca in avcodec_decode_video2 /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libavcodec/utils.c:242:15
    #12 0x50fbaa in hevc_write_frame /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libbpg.c:401:11
    #13 0x50f779 in hevc_decode_frame_internal /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libbpg.c:486:11
    #14 0x50b49c in hevc_decode_start /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libbpg.c:528:11
    #15 0x50b49c in bpg_decoder_decode /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libbpg.c:1860
    #16 0x505406 in main /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/bpgdec.c:332:9
    #17 0x7fd14335fb96 in __libc_start_main /build/glibc-OTsEL5/glibc-2.27/csu/../csu/libc-start.c:310
    #18 0x41a2e9 in _start (/home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/bpgdec+0x41a2e9)

0x6250000000de is located 34 bytes to the left of 8712-byte region [0x625000000100,0x625000002308)
allocated by thread T0 here:
    #0 0x4d8560 in malloc (/home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/bpgdec+0x4d8560)
    #1 0x54b125 in av_malloc /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libavutil/mem.c:138:11
    #2 0x5498ca in avcodec_decode_video2 /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libavcodec/utils.c:242:15
    #3 0x50fbaa in hevc_write_frame /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libbpg.c:401:11
    #4 0x50f779 in hevc_decode_frame_internal /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libbpg.c:486:11
    #5 0x50b49c in hevc_decode_start /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libbpg.c:528:11
    #6 0x50b49c in bpg_decoder_decode /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/libbpg.c:1860
    #7 0x505406 in main /home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/bpgdec.c:332:9
    #8 0x7fd14335fb96 in __libc_start_main /build/glibc-OTsEL5/glibc-2.27/csu/../csu/libc-start.c:310

SUMMARY: AddressSanitizer: heap-buffer-overflow (/home/alex/code-reviww/fuzz/libbpg-all/libbpg-0.9.8/bpgdec+0x4d75c1) in __asan_memcpy
Shadow bytes around the buggy address:
  0x0c4a7fff7fc0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c4a7fff7fd0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c4a7fff7fe0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c4a7fff7ff0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c4a7fff8000: fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa fa
=>0x0c4a7fff8010: fa fa fa fa fa fa fa fa fa fa fa[fa]fa fa fa fa
  0x0c4a7fff8020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c4a7fff8030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c4a7fff8040: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c4a7fff8050: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  0x0c4a7fff8060: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
Shadow byte legend (one shadow byte represents 8 application bytes):
  Addressable:           00
  Partially addressable: 01 02 03 04 05 06 07 
  Heap left redzone:       fa
  Freed heap region:       fd
  Stack left redzone:      f1
  Stack mid redzone:       f2
  Stack right redzone:     f3
  Stack after return:      f5
  Stack use after scope:   f8
  Global redzone:          f9
  Global init order:       f6
  Poisoned by user:        f7
  Container overflow:      fc
  Array cookie:            ac
  Intra object redzone:    bb
  ASan internal:           fe
  Left alloca redzone:     ca
  Right alloca redzone:    cb
```
