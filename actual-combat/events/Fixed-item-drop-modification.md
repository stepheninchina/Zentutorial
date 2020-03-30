# 简单的固定的方块掉落物

这个就是个简单的掉落物修改，运用起来没有那么麻烦


```javascript
import crafttweaker.events.IEventManager;
import crafttweaker.event.BlockHarvestDropsEvent;
// 引用方块采掘掉落事件
import crafttweaker.item.WeightedItemStack;
// 加权物品堆
events.onBlockHarvestDrops(
        function(event as BlockHarvestDropsEvent) {
	    val blockID as string = event.block.definition.id;
            val meta as int = event.block.meta;
		// 定义方块数据      方块的id和meta值
	    if(event.silkTouch) return;
		// 排除精准采集
	    if(blockID == "minecraft:log" && meta == 1) {
		    event.drops = planks;
			// 给掉落定义一个物品堆planks
	    }
    }
);

static planks as WeightedItemStack[] = [
	<minecraft:planks:1> % 60,
    <minecraft:planks:1> * 2 % 30,
    <minecraft:planks:1> * 3 % 10
];
/*
	添加一个planks物品堆，设置概率
	这个实例的整体意思是
	挖云杉原木有100%掉落一个云杉木板
	40%概率额外掉落一个
	10%概率再额外掉落一个
*/
```
