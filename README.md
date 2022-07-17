# howto-compute-cache
 Me learning/teaching to compute cache instead of sequence_data

#### Including
* In your .h file:
```C++
#include "AE_ComputeCacheSuite.h"
```

#### Global Setup
### First we need to setup the Compute Cache Suite in order to use it
* In GlobalSetup():
```C++
AEFX_SuiteScoper<AEGP_ComputeCacheSuite1> cacheSuite = AEFX_SuiteScoper<AEGP_ComputeCacheSuite1>(
		in_data,
		kAEGPComputeCacheSuite,
		kAEGPComputeCacheSuiteVersion1,
		out_data);
```
* Then we need to register any classes <INSERT BETTER DESCRIPTION HERE>

```C++
AEGP_CCComputeClassIdP id = "adobe.ae.effect.test_effect.cache_v_1";
AEGP_ComputeCacheCallbacks *test;

(*cacheSuite->AEGP_ClassRegister)(id, test);
```

#### Global Setdown
### As well as registering our future cache data, we need to de-register it when the plugin is deleted
```C++
ERR(cacheSuite->AEGP_ClassUnregister(id));
```

