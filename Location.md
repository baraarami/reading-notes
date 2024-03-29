

# Location
![](https://www.techwebspace.com/wp-content/uploads/2017/11/2017-11-30.jpg)
## Get the last known location
### How to get the last known location?

1. Set up Google Play services
* Download and install the Google Play services component via the `SDK Manager`.
* Add the library to your project.

2. Specify app permissions by doing request location permissions.

3. Create location services client by adding in OnCreate.

```
 private FusedLocationProviderClient fusedLocationClient;

 // ..

 @Override
 protected void onCreate(Bundle savedInstanceState) {
    // ...

    fusedLocationClient = LocationServices.getFusedLocationProviderClient(this);
 }
```
4. Get the last known location
   - When your app is connected to these you can use the fused location provider's `getLastLocation()` method to retrieve the device location.
   ```
    fusedLocationClient.getLastLocation()
        .addOnSuccessListener(this, new OnSuccessListener<Location>() {
            @Override
            public void onSuccess(Location location) {
                // Got last known location. In some rare situations this can be null.
                if (location != null) {
                    // Logic to handle location object
                }
            }
        });
   ```
5. Maintain a current best estimate
   - To validate the accuracy of a location that's returned from getLastLocation(), complete steps that include the following:

     - Check whether the location retrieved is significantly newer than the previously fetched location.
     - Check whether the accuracy claimed by the location is better or worse than that of the previous estimate.
     - Check the provider that's associated with the new location. Decide whether you trust this provider more than the one used in your app's cached location.













