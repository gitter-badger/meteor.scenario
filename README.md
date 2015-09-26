#A data mockup package for meteor

Meteor package to design and generate application test data. 


## Installation 

Run 'meteor add emmanuelbuah:scenario'

## Proposed Api/Usage
```
 
Assuming the following collections: Users, Post, Comments and following simpleschema's UserSchema, PostSchema and CommentSchema

//Add a single named record to User Collection 
Scenario.Add("Emmanuel", { name: .... , ..}).To(Users);

//Add a multiple named record to User Collection
Scenario.Add([{"Eric" : { name: .... , ..}},{"Nick" : { name: .... , ..}}]).To(Users);

//Add a multiple gen record to User Collection
Scenario.AddRecords(4).To(Users);

//Add a single record to Post Collection by user Emmanuel
Scenario.Add({ title: "My first post"}).To(Posts).Set("CreatedBy").To("Emmanuel");

//Add a multiple record to Post Collection by user Emmanuel, indicating setting createdBy =_id 
Scenario.AddRecords(10).To(Posts).Set("createdBy").To("Emmanuel","_id");

//Add a multiple record to Post Collection randmoizing creator amongts user Emmanuel, Eric and Nick 
Scenario.AddRecords(10).To(Posts).Set("createdBy").RandomizeAmongst("Emmanuel","Eric","Nick"]).As("Posts");

//Reference record to related records
Scenario.ForEachIn("Posts").AddRecords(10).To(Comments).Set("postId").ToParent("_id");

```

## Discussion (Gitter - N/A) 
- Thoughts on Api 
- Identify first set of api to implement




