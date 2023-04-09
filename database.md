
### CTE for get last 3 login
```bash
With cte as (
  SELECT ROW_NUMBER() OVER( PARTITION BY lv.userId ORDER BY lv.created_at DESC, userid, version) row_no, U.name, version, lv.created_at from log_version lv JOIN users u ON U.id = lv.userId
	)
Select * from cte WHERE row_no <= 3
```

### Delete duplicate 

```bash
;with cte as (
select ROW_NUMBER()over(partition by barcode,vendor_id order by id desc) rn ,* from posted_price
) 
delete from cte where rn>1
```

### delete duplicate 2
```bash
delete from [MRP].[dbo].[SeasonConfig] where id in (
SELECT  min([id])
      
FROM [MRP].[dbo].[SeasonConfig]  where deleted_at is null
group by [season_factor]
,[priority]
,[grade]
,[LogisticGroup_ID]
,[level1_ID]
,[level2_ID]
,[level3_ID]
,[level4_ID]
,[level5_ID]
,[itemid]
,[stateid]
,[cityid]
,[Location_ID]
,[expireL1]
,[expireL2]
,[item_bundle_id]
,[location_bundle_id]
,[created_at]
,[updated_at]
,[deleted_at]
 having count(*)>1
)
```
