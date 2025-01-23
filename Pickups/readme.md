# Pickups

## Voorbereiding
Nodig: 
* Unity3D


## Maken van een pick-up-able object
De meest bekende en eenvoudige pickup is de coin van Mario. Deze kun je namaken door een cylinder aan te passen en deze geel maken.
Om de coin er meer uit te laten zien als Mario coin moet je deze animeren. Mario coins roteren altijd. Dit kan je maken door middel van een script. Maak een nieuw script genaamd Pickup. Hang deze op het coin object.

```C#
using UnityEngine;
public class Pickup : MonoBehaviour
{
    void Update()
    {
        transform.Rotate(0, 0, 360*Time.deltaTime);
    }
}

```
Iedere seconde roteert het object waar het script op staat 360 graden.

## Collision
Om een object op te pakken moet je kijken of een object de speler aan raakt. Hier hebben de speler en de Pickup allebei een collider nodig. Ook moet een van de objecten een Rigidbody hebben. Als het goed is heeft jouw speler een Rigidbody.
Jouw speler zou nu moeten botsen met de Coin. 

## Verwijderen na contact
De `Update()` functie wordt iedere frame uitgevoerd. De `Start()` functie wordt alleen de eerste frame uitgevoerd. Er zijn nog veel meer functies die uitgevoerd worden op specifieke momenten. De `OnCollisionEnter(Colllision collision)` functie wordt uitgevoerd wanneer er een collision is. 

```C#
void OnCollisionEnter(Collision collision){
        Debug.Log("we hebben een collision!");
    }
```

Wanneer er een botsing is wordt in de console de tekst uitgeprint. Maar we willen niet dat er tekst uitgeprint wordt, we willen dat het object waar op het script wordt staat wordt verwijdert. Vervang de `Debug` code met 

```C#
Destroy(gameObject);
```