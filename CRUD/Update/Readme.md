<!-- TO UPDATEONE -->
db.cars.updateOne(
    {model :"Nexon"},
    {$set:{color:"Red"}}
);

<!-- RESULT -->
[
  {
    _id: ObjectId('66f0ef074f663e882f9e4c38'),
    maker: 'Tata',
    model: 'Nexon',
    fuel_type: 'Petrol',
    transmission: 'Automatic',
    engine: { type: 'Turbocharged', cc: 1199, torque: '170 Nm' },
    features: [ 'Touchscreen', 'Reverse Camera', 'Bluetooth Connectivity' ],
    sunroof: false,
    airbags: 2,
    color: 'Red'
  }
]


<!-- TO push new THE DATA IN NESTED KEY  means push-->
 db.cars.updateOne( 
    {model:"Nexon"},   //Filter to find the specific document
    {$push:{features:"Heated
 Seats"}}
 )

 RESULT:
 [
  {
    _id: ObjectId('66f0ef074f663e882f9e4c38'),
    maker: 'Tata',
    model: 'Nexon',
    fuel_type: 'Petrol',
    transmission: 'Automatic',
    engine: { type: 'Turbocharged', cc: 1199, torque: '170 Nm' },
    features: [
      'Touchscreen',
      'Reverse Camera',
      'Bluetooth Connectivity',
      'Heated Seats'
    ],
    sunroof: false,
    airbags: 2,
    color: 'Red'
  }
]


<!-- TO PULL THE DATA TO DELETE IT -->
db.cars.updateOne({model:"Nexon"},{$pull:{features:"Heated S
eats"}})

<!-- TO UPDATE THE NESTED DATA -->

 db.cars.updateOne(
... {model:"Nexon"},
... {$set:{"engine.torque":"270 Nm"}}
)
RESULT:
{
  _id: ObjectId('66f0ef074f663e882f9e4c38'),
  maker: 'Tata',
  model: 'Nexon',
  fuel_type: 'Petrol',
  transmission: 'Automatic',
  engine: { type: 'Turbocharged', cc: 1199, torque: '270 Nm' },
  features: [ 'Touchscreen', 'Reverse Camera', 'Bluetooth Connectivity' ],
  sunroof: false,
  airbags: 2,
  color: 'Red'
}

<!-- TO UPDATE MULTIPLE VALUES IN FEATURES KEY we use each operator -->
db.cars.updateMany(
... {model:"Nexon"},
... {$push:
 {features:{$each:["Wireless charging","Voice container"]}}
 })

 Result:
 {
  _id: ObjectId('66f0ef074f663e882f9e4c38'),
  maker: 'Tata',
  model: 'Nexon',
  fuel_type: 'Petrol',
  transmission: 'Automatic',
  engine: { type: 'Turbocharged', cc: 1199, torque: '270 Nm' },
  features: [
    'Touchscreen',
    'Reverse Camera',
    'Bluetooth Connectivity',
    'Wireless charging',
    'Voice container'
  ],
  sunroof: false,
  airbags: 2,
  color: 'Red'
}

<!-- TO remove the color red in nexon mdoel -->
 db.cars.updateOne(
{model:"Nexon"},
 {$unset:{color:"Red"}})

RESULT:
{
  _id: ObjectId('66f0ef074f663e882f9e4c38'),
  maker: 'Tata',
  model: 'Nexon',
  fuel_type: 'Petrol',
  transmission: 'Automatic',
  engine: { type: 'Turbocharged', cc: 1199, torque: '270 Nm' },
  features: [
    'Touchscreen',
    'Reverse Camera',
    'Bluetooth Connectivity',
    'Wireless charging',
    'Voice container'
  ],
  sunroof: false,
  airbags: 2
}

<!-- TO UPDATE FOR ALL DOCUMENTS -->
db.cars.updateMany({},{$set:{color:"Red"}})


In MongoDB, upsert is a feature that allows you to either update an existing document or insert a new one if no matching document is found. This is particularly useful when you want to ensure that a record is created or updated in a single operation

db.cars.updateOne(
    {model:"Venue"},
    {$set:{Maker:"Hyundai"}},{
upsert:true}
)
