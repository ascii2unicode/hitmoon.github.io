--Type <RET> for more, q to quit, c to continue without paging--
62
63              return min(start + __ffs(tmp), nbits);
64      }
65      #endif
66
67      #ifndef find_next_bit
68      /*
69       * Find the next set bit in a memory region.
70       */
71      unsigned long find_next_bit(const unsigned long *addr, unsigned long size,
72                                  unsigned long offset)
73      {
74              return _find_next_bit(addr, NULL, size, offset, 0UL);
   0xffffffff81431790 <+0>:     mov    %rsi,%rax
   0xffffffff81431793 <+3>:     mov    %rdx,%rcx
   0xffffffff81431796 <+6>:     cmp    %rdx,%rsi
   0xffffffff81431799 <+9>:     jbe    0xffffffff814317e9 <find_next_bit+89>

43              tmp = addr1[start / BITS_PER_LONG];
   0xffffffff8143179b <+11>:    mov    %rdx,%rsi
   0xffffffff8143179e <+14>:    mov    $0xffffffffffffffff,%rdx
   0xffffffff814317a5 <+21>:    shr    $0x6,%rsi

44              if (addr2)
45                      tmp &= addr2[start / BITS_PER_LONG];
46              tmp ^= invert;
47
48              /* Handle 1st word. */
49              tmp &= BITMAP_FIRST_WORD_MASK(start);
   0xffffffff814317a9 <+25>:    shl    %cl,%rdx
--Type <RET> for more, q to quit, c to continue without paging--

50              start = round_down(start, BITS_PER_LONG);
   0xffffffff814317ac <+28>:    and    $0xffffffffffffffc0,%rcx

51
52              while (!tmp) {
   0xffffffff814317b0 <+32>:    and    (%rdi,%rsi,8),%rdx
   0xffffffff814317b4 <+36>:    jne    0xffffffff814317da <find_next_bit+74>

53                      start += BITS_PER_LONG;
   0xffffffff814317b6 <+38>:    add    $0x40,%rcx

54                      if (start >= nbits)
   0xffffffff814317ba <+42>:    cmp    %rcx,%rax
   0xffffffff814317bd <+45>:    ja     0xffffffff814317ca <find_next_bit+58>



1. 新加了两个字段 nohz
2.