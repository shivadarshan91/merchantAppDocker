{
"aggrs": [
{
"stages": [
{
"$match": {
"first_name": {
"$var": "first_name"
}
}
},
{
"$group": {
"_id": {
"customer": "$customer_id",
"first_name": "$first_name",
"last_name": "$last_name"
},
"credit": {
"$sum": "$credit"
},
"debit": {
"$sum": "$debit"
}
}
},
{
"$skip": {
"$var": "@skip"
}
},
{
"$limit": {
"$var": "@limit"
}
}
],
"type": "pipeline",
"uri": "ledgerbalance"
}
]
}
