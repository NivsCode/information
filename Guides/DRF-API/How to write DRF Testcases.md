1. [Using faker and factory-boy to write API Test cases](https://medium.com/analytics-vidhya/factoryboy-usage-cd0398fd11d2)
- Create a `tests.py`
- Initialise the following,
	- factories for models (which inherit `from factory.django import DjangoModelFactory` ) with the help of faker library. The documentation for providers is [here](https://faker.readthedocs.io/en/stable/providers.html)
	- A client to handle the requests, `client = APIClient()`
	- Intialise the userfactory, 
```
from django.contrib.auth import get_user_model
User = get_user_model()faker = Factory.create()

class UserFactory(DjangoModelFactory):
	class Meta:
		model = User
		username = faker.user_name()
		email = faker.email()
```
- Write testcases for index and create under `<object>ListTest` inheriting from `APITestCase` and show, update and delete test cases under `<object>detailtest`. A list of assertions can be found [here](https://docs.djangoproject.com/en/4.0/topics/testing/tools/#django.test.Client.get).
```
class ClientListTest(APITestCase):

	def setUp(self):
		self.user = UserFactory()
		self.client_list = ClientFactory.create_batch(2, user=self.user)
	
	
	def test_clients_list_positive(self):
		url = reverse("invoice:list")
		client.force_authenticate(user=self.user)
		response = client.get(url, format="json")
	
		self.assertEqual(response.status_code, status.HTTP_200_OK)
		for c in self.client_list:
			self.assertContains(response, c.name)
```

