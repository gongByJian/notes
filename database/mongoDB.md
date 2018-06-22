

mongoDB in 查询

db.getCollection('MFRong360Data').find({"microfinanceUserId":{"$in":[
"5f222d14b2a24b398cc43ddf74eb0588",
"8f4c08b61b184c2d950f9a566f0d5855"
]}},{"_id":0,"orderNo":1,"microfinanceUserId":1})