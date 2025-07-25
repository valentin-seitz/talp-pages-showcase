SHELL=/bin/sh
BENCHMARK=bt-mz
BENCHMARKU=BT-MZ
F08=def

include ../config/make.def


OBJS = bt.o bt_data.o initialize.o exact_solution.o exact_rhs.o \
       set_constants.o adi.o  rhs.o zone_setup.o  \
       x_solve.o y_solve.o  exch_qbc.o solve_subs.o \
       z_solve.o add.o error.o verify.o setup_mpi.o \
       mpinpb.o error_cond.o alloc_space.o \
       ${COMMON}/print_results.o ${COMMON}/timers.o

include ../sys/make.common

# npbparams.h is included by bt_data module (via bt_data.o)

${PROGRAM}: config ${OBJS}
	${FLINK} ${FLINKFLAGS} -o ${PROGRAM} ${OBJS} ${F_LIB}

.f90.o:
	${FCOMPILE} $<

bt.o:             bt.f90  bt_data.o mpinpb.o
initialize.o:     initialize.f90  bt_data.o
exact_solution.o: exact_solution.f90  bt_data.o
exact_rhs.o:      exact_rhs.f90  bt_data.o
set_constants.o:  set_constants.f90  bt_data.o
adi.o:            adi.f90  bt_data.o
rhs.o:            rhs.f90  bt_data.o
zone_setup.o:     zone_setup.f90  bt_data.o mpinpb.o
x_solve.o:        x_solve.f90  bt_data.o
y_solve.o:        y_solve.f90  bt_data.o
z_solve.o:        z_solve.f90  bt_data.o
solve_subs.o:     solve_subs.f90
add.o:            add.f90  bt_data.o
error.o:          error.f90  bt_data.o
verify.o:         verify.f90  bt_data.o mpinpb.o
exch_qbc.o:       exch_qbc.f90  bt_data.o mpinpb.o
setup_mpi.o:      setup_mpi.f90  bt_data.o mpinpb.o
error_cond.o:     error_cond.f90  mpinpb.o
alloc_space.o:    alloc_space.f90  bt_data.o mpinpb.o
bt_data.o:        bt_data.f90  npbparams.h
mpinpb.o:         mpinpb.f90  bt_data.o
mpinpb.f90:       mpinpb_${F08}.f90
	cp mpinpb_${F08}.f90 $@

clean:
	- rm -f *.o *~ *.mod mputil* core
	- rm -f npbparams.h mpinpb.f90
