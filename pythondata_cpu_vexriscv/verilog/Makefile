SRC := ${shell find . -type f -name \*.scala}

all: VexRiscv.v VexRiscv_Debug.v VexRiscv_Lite.v VexRiscv_LiteDebug.v VexRiscv_IMAC.v VexRiscv_IMACDebug.v VexRiscv_Min.v VexRiscv_MinDebug.v VexRiscv_Full.v VexRiscv_FullDebug.v VexRiscv_Linux.v VexRiscv_LinuxDebug.v VexRiscv_LinuxNoDspFmax.v VexRiscv_Secure.v VexRiscv_SecureDebug.v 

VexRiscv.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault"

VexRiscv_Debug.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault -d --outputFile VexRiscv_Debug"

VexRiscv_Lite.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault --iCacheSize 2048 --dCacheSize 0 --mulDiv true --singleCycleShift false --singleCycleMulDiv false  --outputFile VexRiscv_Lite"

VexRiscv_LiteDebug.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault -d --iCacheSize 2048 --dCacheSize 0 --mulDiv true --singleCycleShift false --singleCycleMulDiv false --outputFile VexRiscv_LiteDebug"

VexRiscv_IMAC.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault --csrPluginConfig all --atomics true --compressedGen true --outputFile VexRiscv_IMAC"

VexRiscv_IMACDebug.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault --csrPluginConfig all --atomics true --compressedGen true -d --outputFile VexRiscv_IMACDebug"

VexRiscv_Min.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault --iCacheSize 0 --dCacheSize 0 --mulDiv false --singleCycleShift false --singleCycleMulDiv false --bypass false --prediction none --outputFile VexRiscv_Min"

VexRiscv_MinDebug.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault -d --iCacheSize 0 --dCacheSize 0 --mulDiv false --singleCycleShift false --singleCycleMulDiv false --bypass false --prediction none --outputFile VexRiscv_MinDebug"

VexRiscv_Full.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault --csrPluginConfig all --outputFile VexRiscv_Full"

VexRiscv_FullDebug.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault --csrPluginConfig all -d --outputFile VexRiscv_FullDebug"

VexRiscv_Linux.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault --csrPluginConfig linux-minimal --outputFile VexRiscv_Linux"

VexRiscv_LinuxDebug.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault --csrPluginConfig linux-minimal -d --outputFile VexRiscv_LinuxDebug"

VexRiscv_LinuxNoDspFmax.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault --csrPluginConfig linux-minimal --singleCycleMulDiv=false --relaxedPcCalculation=true --prediction=none --outputFile VexRiscv_LinuxNoDspFmax"

VexRiscv_Secure.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault --pmp true --csrPluginConfig secure --outputFile VexRiscv_Secure"

VexRiscv_SecureDebug.v: $(SRC)
	sbt compile "runMain vexriscv.GenCoreDefault --pmp true --csrPluginConfig secure -d --outputFile VexRiscv_SecureDebug"
