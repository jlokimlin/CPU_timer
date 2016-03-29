# **cpu\_timer**

This Fortran project implements a class for computing elapsed CPU time. More specifically, you can determine the CPU time consumed by a particular piece of your code, that is:

```fortran

	!... start timer
	
	do i = 1, n
		
		!...some big calculation...
	
	end do
	
	!...stop timer
	
	print *, 'Elapsed CPU time = ', blah
```

-----------------------------------------------------------------------------

## Requirements
* The GNU Make tool https://www.gnu.org/software/make/
* The GNU gfortran compiler https://gcc.gnu.org/wiki/GFortran

-----------------------------------------------------------------------------

## To build the project

Type the following command line arguments
```
git clone https://github.com/jlokimlin/cpu_timer.git

cd cpu_timer; make all
```

-----------------------------------------------------------------------------

## Usage:

```fortran

use, intrinsic :: iso_fortran_env, only: &
    wp => REAL64, &
    ip => INT32

use type_CpuTimer, only: &
    CpuTimer

! Explicit typing only
implicit none

type (CpuTimer)         :: timer
real (wp)               :: wall_clock_time
real (wp)	            :: total_processor_time
integer (ip), parameter :: UNITS = 0 ! (optional argument) = 0 for seconds, or 1 for minutes, or 2 for hours

! Starting the timer
call timer%start()

! Stopping the timer
call timer%stop()

! Reading the time
wall_clock_time = timer%get_elapsed_time( UNITS )

total_processor_time = timer%get_total_cpu_time( UNITS )

! Put a time stamp
call timer%print_time_stamp()

```

-----------------------------------------------------------------------------

## Result

```
	
	Demonstrate the usage of TYPE(CpuTimer).
	
	March 29 2016  11:49:48.033 AM
	
	*********************************************
	
	 TIME_RANDOM_NUMBER_ROUTINE
	
	 times the intrinsic RANDOM_NUMBER routine:
	
	    call random_number( x(1:n) )
	
	  Data vectors will be of minimum size              1
	  Data vectors will be of maximum size        1048576
	  Number of repetitions of the operation:           5
	
	  Timing results:
	
	       Size    Rep #1         Rep #2         Rep #3         Rep #4         Rep #5         MINVAL         SUM            MAXVAL         
	
	          1    2.19950E-02    1.89980E-02    1.79970E-02    1.89970E-02    1.79970E-02    1.79970E-02    1.91968E-02    2.19950E-02
	          2    1.79970E-02    1.89980E-02    1.79970E-02    1.79970E-02    1.89970E-02    1.79970E-02    1.83972E-02    1.89980E-02
	          4    1.79970E-02    1.79980E-02    1.79970E-02    1.89970E-02    1.79970E-02    1.79970E-02    1.81972E-02    1.89970E-02
	          8    1.79980E-02    1.89970E-02    1.79970E-02    1.79970E-02    1.79980E-02    1.79970E-02    1.81974E-02    1.89970E-02
	         16    1.89970E-02    1.79970E-02    1.79970E-02    1.89970E-02    1.79980E-02    1.79970E-02    1.83972E-02    1.89970E-02
	         32    1.79970E-02    1.89970E-02    1.79970E-02    1.79970E-02    1.79980E-02    1.79970E-02    1.81972E-02    1.89970E-02
	         64    1.89970E-02    1.79970E-02    1.79970E-02    1.89980E-02    1.79970E-02    1.79970E-02    1.83972E-02    1.89980E-02
	        128    1.89970E-02    1.79970E-02    1.79970E-02    1.89980E-02    1.79970E-02    1.79970E-02    1.83972E-02    1.89980E-02
	        256    1.79970E-02    1.79970E-02    1.89970E-02    1.79980E-02    1.79970E-02    1.79970E-02    1.81972E-02    1.89970E-02
	        512    1.89970E-02    1.79970E-02    1.79980E-02    1.89970E-02    1.79970E-02    1.79970E-02    1.83972E-02    1.89970E-02
	       1024    1.79970E-02    1.79970E-02    1.89980E-02    1.79970E-02    1.89970E-02    1.79970E-02    1.83972E-02    1.89980E-02
	       2048    1.79970E-02    1.79980E-02    1.79970E-02    1.89970E-02    1.79970E-02    1.79970E-02    1.81972E-02    1.89970E-02
	       4096    1.79970E-02    1.89980E-02    1.79970E-02    1.79970E-02    1.89970E-02    1.79970E-02    1.83972E-02    1.89980E-02
	       8192    1.79970E-02    1.79980E-02    1.89970E-02    1.79970E-02    1.79970E-02    1.79970E-02    1.81972E-02    1.89970E-02
	      16384    1.79980E-02    1.89970E-02    1.79970E-02    1.79970E-02    1.89970E-02    1.79970E-02    1.83972E-02    1.89970E-02
	      32768    1.79980E-02    1.89970E-02    1.89970E-02    1.79970E-02    1.79970E-02    1.79970E-02    1.83972E-02    1.89970E-02
	      65536    1.89970E-02    1.79980E-02    1.79970E-02    1.89970E-02    1.79970E-02    1.79970E-02    1.83972E-02    1.89970E-02
	     131072    1.79980E-02    1.79970E-02    1.89970E-02    1.79970E-02    1.79980E-02    1.79970E-02    1.81974E-02    1.89970E-02
	     262144    1.89970E-02    1.79970E-02    1.79970E-02    1.79970E-02    1.89980E-02    1.79970E-02    1.83972E-02    1.89980E-02
	     524288    1.79970E-02    1.79970E-02    1.89970E-02    1.79970E-02    1.79980E-02    1.79970E-02    1.81972E-02    1.89970E-02
	    1048576    1.89970E-02    1.79970E-02    1.79970E-02    1.89970E-02    1.79980E-02    1.79970E-02    1.83972E-02    1.89970E-02
	
	*********************************************
	
	  TIME_VECTORIZED_EXP_ROUTINE:
	
	    y(1:n) = x(1:n)  
	    y(1:n) = PI * x(1:n)  
	    y(1:n) = sqrt( x(1:n) )
	    y(1:n) = exp( x(1:n) )
	
	  Data vectors will be of minimum size           4096
	  Data vectors will be of maximum size        4194304
	  Number of repetitions of the operation:           5
	
	  Timing results:
	
	       Size    Rep #1         Rep #2         Rep #3         Rep #4         Rep #5         
	
	       4096    1.79970E-02    1.29980E-02    1.29990E-02    1.19980E-02    1.19980E-02
	       8192    1.29980E-02    1.19980E-02    1.29980E-02    1.19990E-02    1.19980E-02
	      16384    1.29980E-02    1.29980E-02    1.19990E-02    1.29980E-02    1.29980E-02
	      32768    1.19980E-02    1.29980E-02    1.29980E-02    1.19980E-02    1.29980E-02
	      65536    1.19980E-02    1.19980E-02    1.29980E-02    1.29980E-02    1.29980E-02
	     131072    1.29980E-02    1.29980E-02    1.19980E-02    1.29980E-02    1.19980E-02
	     262144    1.29980E-02    1.29980E-02    1.19990E-02    1.19980E-02    1.29980E-02
	     524288    1.29980E-02    1.19990E-02    1.29980E-02    1.19980E-02    1.29980E-02
	    1048576    1.29980E-02    1.29980E-02    1.29980E-02    1.19980E-02    1.19980E-02
	    2097152    1.29980E-02    1.29980E-02    1.29980E-02    1.29980E-02    1.19980E-02
	    4194304    1.29980E-02    1.29980E-02    1.29980E-02    1.29980E-02    1.19980E-02
	
	  Timing results:
	
	       Size    Rep #1         Rep #2         Rep #3         Rep #4         Rep #5         
	
	       4096    5.99900E-03    6.99900E-03    6.99900E-03    6.99800E-03    6.99900E-03
	       8192    6.99800E-03    6.99900E-03    6.99900E-03    6.99900E-03    5.99900E-03
	      16384    6.99900E-03    5.99900E-03    6.99900E-03    6.99900E-03    6.99900E-03
	      32768    6.99900E-03    5.99900E-03    6.99900E-03    6.99900E-03    6.99900E-03
	      65536    6.99900E-03    5.99900E-03    5.99900E-03    6.99900E-03    6.99900E-03
	     131072    6.99900E-03    5.99900E-03    6.99900E-03    6.99900E-03    6.99900E-03
	     262144    6.99900E-03    6.99900E-03    6.99900E-03    6.99900E-03    6.99900E-03
	     524288    6.99900E-03    5.99900E-03    5.99900E-03    6.99900E-03    6.99900E-03
	    1048576    6.99900E-03    6.99900E-03    5.99900E-03    6.99900E-03    6.99900E-03
	    2097152    6.99900E-03    6.99900E-03    6.99900E-03    6.99900E-03    6.99900E-03
	    4194304    6.99900E-03    6.99900E-03    6.99900E-03    6.99900E-03    6.99900E-03
	
	  Timing results:
	
	       Size    Rep #1         Rep #2         Rep #3         Rep #4         Rep #5         
	
	       4096    2.49960E-02    2.39960E-02    2.49960E-02    2.49960E-02    2.49970E-02
	       8192    2.49960E-02    2.49960E-02    2.49960E-02    2.39960E-02    2.49960E-02
	      16384    2.39960E-02    2.39970E-02    2.39960E-02    2.49960E-02    2.49960E-02
	      32768    2.39960E-02    2.39960E-02    2.49960E-02    2.39960E-02    2.39970E-02
	      65536    2.39970E-02    2.39960E-02    2.39970E-02    2.39970E-02    2.39960E-02
	     131072    2.39960E-02    2.49970E-02    2.49960E-02    2.49960E-02    2.49960E-02
	     262144    2.39960E-02    2.49960E-02    2.49960E-02    2.49960E-02    2.49970E-02
	     524288    2.49970E-02    2.49960E-02    2.49960E-02    2.49960E-02    2.49960E-02
	    1048576    2.49960E-02    2.59960E-02    2.49960E-02    2.39970E-02    2.49960E-02
	    2097152    2.39960E-02    2.49970E-02    2.49960E-02    2.39960E-02    2.39970E-02
	    4194304    2.39970E-02    2.49960E-02    2.49960E-02    2.49960E-02    2.39960E-02
	
	  Timing results:
	
	       Size    Rep #1         Rep #2         Rep #3         Rep #4         Rep #5         
	
	       4096    1.32979E-01    1.32980E-01    1.32980E-01    1.32980E-01    1.33980E-01
	       8192    1.33979E-01    1.33980E-01    1.33980E-01    1.34979E-01    1.34980E-01
	      16384    1.32980E-01    1.33980E-01    1.33980E-01    1.31980E-01    1.33979E-01
	      32768    1.33980E-01    1.33980E-01    1.32980E-01    1.33979E-01    1.33980E-01
	      65536    1.32980E-01    1.34980E-01    1.32980E-01    1.33980E-01    1.33980E-01
	     131072    1.33980E-01    1.32980E-01    1.33979E-01    1.34979E-01    1.33980E-01
	     262144    1.33979E-01    1.32980E-01    1.32979E-01    1.33980E-01    1.33980E-01
	     524288    1.34979E-01    1.32980E-01    1.33980E-01    1.36980E-01    1.33980E-01
	    1048576    1.31980E-01    1.32980E-01    1.32980E-01    1.33980E-01    1.32980E-01
	    2097152    1.33979E-01    1.33979E-01    1.32980E-01    1.32980E-01    1.32980E-01
	    4194304    1.32979E-01    1.32980E-01    1.32980E-01    1.32980E-01    1.33980E-01
	
	*********************************************
	
	 TIME_UNVECTORIZED_EXP_ROUTINE
	
	    do i = 1, n
	      y(i) = x(i)  
	      y(i) = PI * x(i)  
	      y(i) = sqrt( x(i) )
	      y(i) = exp( x(i) )
	    end do
	
	  Data vectors will be of minimum size           4096
	  Data vectors will be of maximum size        4194304
	  Number of repetitions of the operation:           5
	
	*********************************************
	
	  Timing results:
	
	       Size    Rep #1         Rep #2         Rep #3         Rep #4         Rep #5         
	
	       4096    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	       8192    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	      16384    1.00000E-03    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	      32768    0.00000E+00    1.00000E-03    0.00000E+00    0.00000E+00    0.00000E+00
	      65536    9.99000E-04    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	     131072    1.00000E-03    1.00000E-03    0.00000E+00    0.00000E+00    1.00000E-03
	     262144    1.00000E-03    2.00000E-03    1.00000E-03    1.00000E-03    2.00000E-03
	     524288    2.99900E-03    1.99900E-03    3.00000E-03    2.00000E-03    1.99900E-03
	    1048576    4.99900E-03    4.00000E-03    4.99900E-03    3.99900E-03    4.00000E-03
	    2097152    9.99900E-03    9.99900E-03    9.99800E-03    8.99900E-03    8.99900E-03
	    4194304    2.19960E-02    1.69980E-02    1.79970E-02    1.79980E-02    1.79970E-02
	
	*********************************************
	
	  Timing results:
	
	       Size    Rep #1         Rep #2         Rep #3         Rep #4         Rep #5         
	
	       4096    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	       8192    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	      16384    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	      32768    1.00000E-03    1.00000E-03    0.00000E+00    0.00000E+00    0.00000E+00
	      65536    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    1.00000E-03
	     131072    1.00000E-03    1.00000E-03    1.00000E-03    1.00000E-03    1.00000E-03
	     262144    1.00000E-03    1.00000E-03    1.00000E-03    1.00000E-03    1.00000E-03
	     524288    2.00000E-03    2.00000E-03    1.99900E-03    2.00000E-03    2.00000E-03
	    1048576    3.99900E-03    3.99900E-03    4.00000E-03    4.00000E-03    3.99900E-03
	    2097152    7.99800E-03    8.99800E-03    7.99900E-03    8.99800E-03    7.99900E-03
	    4194304    1.79970E-02    1.79970E-02    1.69980E-02    1.79970E-02    1.69980E-02
	
	*********************************************
	
	  Timing results:
	
	       Size    Rep #1         Rep #2         Rep #3         Rep #4         Rep #5         
	
	       4096    0.00000E+00    0.00000E+00    0.00000E+00    9.99000E-04    0.00000E+00
	       8192    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	      16384    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	      32768    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	      65536    0.00000E+00    1.00000E-03    0.00000E+00    1.00000E-03    9.99000E-04
	     131072    0.00000E+00    1.00000E-03    0.00000E+00    1.00000E-03    1.00000E-03
	     262144    2.00000E-03    1.99900E-03    1.99900E-03    2.00000E-03    2.00000E-03
	     524288    2.99900E-03    2.99900E-03    2.99900E-03    3.00000E-03    2.99900E-03
	    1048576    5.99900E-03    6.99800E-03    5.99900E-03    5.99900E-03    5.99900E-03
	    2097152    1.29980E-02    1.29980E-02    1.29980E-02    1.19980E-02    1.19980E-02
	    4194304    2.59960E-02    2.49960E-02    2.49970E-02    2.49960E-02    2.49970E-02
	
	*********************************************
	
	  Timing results:
	
	       Size    Rep #1         Rep #2         Rep #3         Rep #4         Rep #5         
	
	       4096    9.99000E-04    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	       8192    0.00000E+00    0.00000E+00    0.00000E+00    9.99000E-04    0.00000E+00
	      16384    1.00000E-03    1.00000E-03    1.00000E-03    1.00000E-03    0.00000E+00
	      32768    1.00000E-03    1.99900E-03    1.00000E-03    1.00000E-03    1.00000E-03
	      65536    1.99900E-03    2.00000E-03    1.99900E-03    3.00000E-03    2.00000E-03
	     131072    3.99900E-03    4.99900E-03    4.99900E-03    4.99900E-03    3.99900E-03
	     262144    8.99800E-03    8.99900E-03    8.99800E-03    8.99900E-03    8.99900E-03
	     524288    1.79970E-02    1.79980E-02    1.79970E-02    1.79970E-02    1.89970E-02
	    1048576    3.69950E-02    3.59940E-02    3.59950E-02    3.69940E-02    3.69940E-02
	    2097152    7.39890E-02    7.39890E-02    7.39890E-02    7.39890E-02    7.39880E-02
	    4194304    1.46978E-01    1.46977E-01    1.47978E-01    1.47978E-01    1.46977E-01
	
	*********************************************
	
	  TIME_2D_NEAREST_NEIGHBOR_PROBLEM
	
	  Given x(2,n) and y(2),
	
	    find x(2,*) closest to y(2).
	
	    do i = 1, n
	      if distance( x(2,i), y ) < minimum so far
	        x_min = x(2,i)
	    end do
	
	  Data vectors will be of minimum size           1024
	  Data vectors will be of maximum size        1048576
	  Number of repetitions of the operation:           5
	
	  Timing results:
	
	       Size    Rep #1         Rep #2         Rep #3         Rep #4         Rep #5         
	
	       1024    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	       2048    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	       4096    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	       8192    1.00000E-03    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	      16384    0.00000E+00    0.00000E+00    0.00000E+00    1.00000E-03    0.00000E+00
	      32768    0.00000E+00    0.00000E+00    1.00000E-03    0.00000E+00    0.00000E+00
	      65536    9.99000E-04    1.00000E-03    0.00000E+00    0.00000E+00    1.00000E-03
	     131072    1.00000E-03    9.99000E-04    9.99000E-04    1.99900E-03    1.00000E-03
	     262144    2.00000E-03    2.00000E-03    3.00000E-03    2.00000E-03    1.99900E-03
	     524288    4.99900E-03    4.99900E-03    4.99900E-03    4.99900E-03    4.99900E-03
	    1048576    9.99900E-03    9.99900E-03    8.99900E-03    9.99900E-03    9.99900E-03
	
	*********************************************
	
	  TIME_MATRIX_MULTIPLICATION_PROBLEM
	
	  Compute C = A * B
	
	  where
	    A is an L by M matrix,
	    B is an M by N matrix,
	  and so
	    C is an L by N matrix.
	
	  Minimum value of L = M = N =                      4
	  Maximum value of L = M = N =                   1024
	  Number of repetitions of the operation:           5
	
	  Use nested DO loops for matrix multiplication.
	
	  Timing results using nested DO loops:
	
	       Size    Rep #1         Rep #2         Rep #3         Rep #4         Rep #5         
	
	          4    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	         16    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	         64    5.99900E-03    4.99900E-03    5.99900E-03    5.99900E-03    4.99900E-03
	        256    3.45947E-01    3.54945E-01    3.47948E-01    3.46947E-01    3.46947E-01
	       1024    2.25506E+01    2.34194E+01    2.34124E+01    2.33704E+01    2.33944E+01
	
	  Use the MATMUL routine for matrix multiplication.
	
	  Timing results using MATMUL:
	
	       Size    Rep #1         Rep #2         Rep #3         Rep #4         Rep #5         
	
	          4    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	         16    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00    0.00000E+00
	         64    0.00000E+00    0.00000E+00    1.00000E-03    0.00000E+00    0.00000E+00
	        256    8.99800E-03    8.99900E-03    8.99800E-03    8.99900E-03    8.99800E-03
	       1024    5.69914E-01    5.69914E-01    5.68913E-01    5.68913E-01    5.84911E-01
	
	 TYPE (CpuTimer) tests.
	
	 Normal end of execution.
	
	March 29 2016  11:52:23.071 AM
	
	This file was compiled by GCC version 5.1.0 
```