# Streaming API with MuleSoft
 This is a MuleSoft project showing how to use the Salesforce Connector with the Streaming API. It covers the usage of 6 of the 8 operations that are provided out-of-the-box.

# Prerequisites
- Salesforce
- Anypoint Studio
- Salesforce Connector v10.14

# Setup
## Change Data Capture
1. Setup > Integrations > Change Data Capture
2. Select **Contact** from **Available Entities** and move to **Selected Entities**
3. Click **Save**

## Streaming Events
1. Click **App Launcher**
2. Search for **Stream** and click on **Streaming Channels**
3. Click on **New**
4. Create **Streaming Channel Name** (e.g. /u/TestChannel)
5. Assign **Owner Name** or leave the default value.
6. Enter **Description**

## Push Topic
1. Developer Console
2. Debug > Open Execute Anonymous Window
3. Paste in following Apex Code
```
PushTopic pushTopic = new PushTopic();
pushTopic.Name = 'ContactTopic';
pushTopic.Query = 'SELECT Id,FirstName,LastName,Email FROM Contact';
pushTopic.ApiVersion = 47.0;
pushTopic.NotifyForOperationCreate = true;
pushTopic.NotifyForOperationUpdate = true;
pushTopic.NotifyForOperationUndelete = true;
pushTopic.NotifyForOperationDelete = true;
pushTopic.NotifyForFields =  'All';
insert pushTopic;
```
4. Click on **Execute**

## Platform Events
1. Setup > Integrations > Platform Events
2. Click on **New Platform Event**
3. Fill in **Label**
4. Fill in **Plural Label**
5. Click on **Save**
6. Optional - Click on **New** under **Custom Fields & Relationships** and add any custom fields to the object