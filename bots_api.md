# Bots Api
#### _Please read General API Information first_
### Black List for bot pairs (Permission: BOTS_READ, Security: SIGNED)
```
GET /ver1/bots/pairs_black_list
```
**Weight:**
1

**Parameters:**
NONE
### Create or Update pairs BlackList for bots (Permission: BOTS_WRITE, Security: SIGNED)
```
POST /ver1/bots/update_pairs_black_list
```
**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Values(default) | Description
------------ | ------------ | ------------ | ------------ | ------------
pairs | array[string] | YES |   | 
### Create bot (Permission: BOTS_WRITE, Security: SIGNED)
```
POST /ver1/bots/create_bot
```
**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Values(default) | Description
------------ | ------------ | ------------ | ------------ | ------------
name | string | YES |   | 
account_id | integer | YES |   | id from GET /ver1/accounts
pairs | array[string] | YES |   | 
max_active_deals | integer | NO |  (1) | 
base_order_volume | number | YES |   | Base trade size
base_order_volume_type | string | NO | quote_currency, base_currency, percent, xbt  | base order volume currency
take_profit | number | YES |   | Target profit(percentage)
safety_order_volume | number | YES |   | Safety trade size
safety_order_volume_type | string | NO | quote_currency, base_currency, percent, xbt  | safety order volume currency
martingale_volume_coefficient | number | YES |  (1) | 
martingale_step_coefficient | number | YES |  (1) | 
max_safety_orders | integer | YES |   | Max safety trades count
active_safety_orders_count | integer | YES |   | Max active safety trades count
stop_loss_percentage | number | NO |   | 
cooldown | number | NO |   | 
btc_price_limit | number | NO |   | 
strategy | string | NO | short, long (long) | 
safety_order_step_percentage | number | YES |   | Price deviation to open safety trades(percentage)
take_profit_type | string | YES |   | Percentage: base – from base trade, total – from total volume
strategy_list | array[json] | YES |   | For manual signals: [{"strategy":"nonstop"}] or []<br>                                                        For non-stop(1 pair only): [{"strategy":"nonstop"}]<br>                                                        QFL: {"options"=>{"type"=>"original"}, "strategy"=>"qfl"}] <br>                                                        TradingView: [{"options"=>{"time"=>"5m", "type"=>"buy_or_strong_buy"}, "strategy"=>"trading_view"} 
### User bots (Permission: BOTS_READ, Security: SIGNED)
```
GET /ver1/bots
```
**Weight:**
1

**Parameters:**
NONE
### Get bot stats (Permission: BOTS_READ, Security: SIGNED)
```
GET /ver1/bots/stats
```
**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Values(default) | Description
------------ | ------------ | ------------ | ------------ | ------------
account_id | integer | NO |   | Account to show on. Null - show for all. Gather this from GET /ver1/accounts
bot_id | integer | NO |   | Bots to show on. Null - show for all
### Edit bot (Permission: BOTS_WRITE, Security: SIGNED)
```
PATCH /ver1/bots/{bot_id}/update
```
**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Values(default) | Description
------------ | ------------ | ------------ | ------------ | ------------
name | string | YES |   | 
pairs | array[string] | YES |   | 
max_active_deals | integer | NO |  (1) | 
base_order_volume | number | YES |   | Base trade size
base_order_volume_type | string | NO | quote_currency, base_currency, percent, xbt  | base order volume currency
take_profit | number | YES |   | Target profit(percentage)
safety_order_volume | number | YES |   | Safety trade size
safety_order_volume_type | string | NO | quote_currency, base_currency, percent, xbt  | safety order volume currency
martingale_volume_coefficient | number | YES |  (1) | 
martingale_step_coefficient | number | YES |  (1) | 
max_safety_orders | integer | YES |   | Max safety trades count
active_safety_orders_count | integer | YES |   | Max active safety trades count
stop_loss_percentage | number | NO |   | 
cooldown | number | NO |   | 
btc_price_limit | number | NO |   | 
safety_order_step_percentage | number | YES |   | Price deviation to open safety trades(percentage)
take_profit_type | string | YES | total, base (total) | Percentage: base – from base trade, total – from total volume
strategy_list | array[json] | YES |   | For manual signals: [{"strategy":"nonstop"}] or []<br>                                                          For non-stop(1 pair only): [{"strategy":"nonstop"}]<br>                                                          QFL: {"options"=>{"type"=>"original"}, "strategy"=>"qfl"}] <br>                                                          TradingView: [{"options"=>{"time"=>"5m", "type"=>"buy_or_strong_buy"}, "strategy"=>"trading_view"} 
bot_id | integer | YES |   | 
### Disable bot (Permission: BOTS_WRITE, Security: SIGNED)
```
POST /ver1/bots/{bot_id}/disable
```
**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Values(default) | Description
------------ | ------------ | ------------ | ------------ | ------------
bot_id | integer | YES |   | 
### Enable bot (Permission: BOTS_WRITE, Security: SIGNED)
```
POST /ver1/bots/{bot_id}/enable
```
**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Values(default) | Description
------------ | ------------ | ------------ | ------------ | ------------
bot_id | integer | YES |   | 
### Start new deal asap (Permission: BOTS_WRITE, Security: SIGNED)
```
POST /ver1/bots/{bot_id}/start_new_deal
```
**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Values(default) | Description
------------ | ------------ | ------------ | ------------ | ------------
pair | string | NO |   | Can be omited for simple bot
skip_signal_checks | boolean | NO |   | If false or not specified then all paramaters like signals or volume filters will be checked. If true - those checks will be skipped
skip_open_deals_checks | boolean | NO |   | If true then you will be allowed to open more then one deal per pair in composite bot
bot_id | integer | YES |   | 
### Delete bot (Permission: BOTS_WRITE, Security: SIGNED)
```
POST /ver1/bots/{bot_id}/delete
```
**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Values(default) | Description
------------ | ------------ | ------------ | ------------ | ------------
bot_id | integer | YES |   | 
### Panic sell all bot deals (Permission: BOTS_WRITE, Security: SIGNED)
```
POST /ver1/bots/{bot_id}/panic_sell_all_deals
```
**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Values(default) | Description
------------ | ------------ | ------------ | ------------ | ------------
bot_id | integer | YES |   | 
### Cancel all bot deals (Permission: BOTS_WRITE, Security: SIGNED)
```
POST /ver1/bots/{bot_id}/cancel_all_deals
```
**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Values(default) | Description
------------ | ------------ | ------------ | ------------ | ------------
bot_id | integer | YES |   | 
### Bot info (Permission: BOTS_READ, Security: SIGNED)
```
GET /ver1/bots/{bot_id}/show
```
**Weight:**
1

**Parameters:**

Name | Type | Mandatory | Values(default) | Description
------------ | ------------ | ------------ | ------------ | ------------
bot_id | integer | YES |   | 
# Response Entities 
### BotEntity
 ``` 
 {
id: 5                                     
account_id: 10                            
is_enabled: true                          
max_safety_orders: 5                      
active_safety_orders_count: 2             
pairs: ['BTC_LTC', 'BTC_ETH', 'BTC_ADA'] Format: [QUOTE_BASE, ...] 
strategy_list: [{'options'=>{'time'=>'5m', 'type'=>'buy_or_strong_buy'}, 'strategy'=>'trading_view'}, ...] 
max_active_deals: 2                       
active_deals_count: 2                     
deletable?: true                          
created_at: 2018-08-08 08:08:08           
updated_at: 2018-08-10 10:10:10           
name: 'Test Bot'                          
take_profit: '1.5'                       'Percentage' 
base_order_volume: '0.002'                
safety_order_volume: '0.0015'             
safety_order_step_percentage: '1.1'       
take_profit_type: 'base_order_volume'    Values: base_order_volume, total_bought_volume 
type: 'Bot::SingleBot'                   Values: ["Bot::MultiBot", "Bot::SingleBot", "Bot::SwitchBot", "Bot::BitmexBot"] 
martingale_volume_coefficient: '1.3'      
martingale_step_coefficient: '0.9'        
stop_loss_percentage: '5.5'               
cooldown: '200'                           
strategy: 'long'                         Values: long, short 
min_volume_btc_24h: '500.5'               
profit_currency: 'quote_currency'        Values: quote_currency, base_currency 
min_price: '0.0245'                       
max_price: '0.0123'                       
safety_order_volume_type: 'base_currency'Values: quote_currency, base_currency, percent, xbt 
base_order_volume_type: 'percent'        Values: quote_currency, base_currency, percent, xbt 
account_name: 'My account'                
} 
 ``` 