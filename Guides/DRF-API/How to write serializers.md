# Custom serializers

- There are two ways of doing this, using either the `serializers.ModelSerializer` (shortcut) or `serializers.Serializer`
#### `serializers.ModelSerializer` (shortcut) 
```
# This intialises the model attributes and create() and update() by default.
class ClientSerializer(serializers.ModelSerializer):
	class Meta:
		model = Client
		fields = ('id', 'name', 'address', 'currency',)
```

#### `serializers.Serializer` method
```

class ClientSerializer(serializers.Serializer):
	id = serializers.IntegerField(read_only=True)
	name = serializers.IntegerField(max_length=128, default= Client.DEFAULT_NAME)
	address = serializers.CharField()
	currency = serializers.ChoiceField(Client.CURRENCY_CHOICES, default=Client.DEFAULT_CURRENCY)

	def create(self, validated_data):	
	"""
	Create and return a new 'Client' instance, given the validated data.
	"""
		return Client.objects.create(**validated_data)
	
	def update(self, instance, validated_data):
	"""
	Update and return a new 'Client' instance, given the validated data.
	"""
		instance.name = validated_data.get('name', instance.name)
		instance.address = validated_data.get('address', instance.address)
		instance.currency = validated_data.get('currency', instance.currency)
		instance.save()
		return instance
```

- Separate the serializer method for separate functions: Update, etc.

