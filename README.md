# AutoPickupAPI
API for [AutoPickup plugin](https://polymart.org/resource/153)

You can use this .jar file in your build environment to create your own StorageHook implementation and register it with AutoPickup thorugh AutoPickupAPI.

## getting an instance of AutoPickup.
You can obtain an instance of AutoPickup as:
```
		AutoPickupAPI autoPickupAPI = AutoPickupAPI.getInstance();
		if (autoPickupAPI != null) {
			StorageHook myStorageHook = new MyStorateHook();
			autoPickupAPI.registerStorageHook(myStorageHook);
		}
```

If you have a custom storage plugin like backpack, virtual vault, etc, you can implement ```StorageHook``` interface like:
```
public class MyStorageHook implements StorageHook {
	//...
	
	@Override
	public Map<Integer, ItemStack> addItems(Player p, ItemStack... items) {
		// add the provided items into player p's storage,
		// whatever could not store in the storage should be returned as the leftover.

		Map<Integer, ItemStack> leftover;
		// leftover = yourStoragePlugin.addItems(p, items);

		return leftover;
	}

	@Override
	public void autoBlock(Player p) {
		// do your own auto blocking implementation for your storage.
	}
}
```
