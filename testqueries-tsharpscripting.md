

# Query ID - TS0001

## Category
T-Sharp Scripting

## Query Text
How do I make the skybox for my scene rotate on every frame, creating a dynamic background effect in T#? Help me generate a script for the same

## Expected Answer
The code below helps you rotate the skybox every frame in the Update() function at a speed of 1.5 units. 

### Code
```csharp
// The code below rotates the SkyBox per frame
using System;
using System.Collections;
using Terra.Studio;
using Terra.Studio.Exposed;
using Terra.Studio.Exposed.Layers;
using UnityEngine;

public class SkyboxRotator : StudioBehaviour
{
    private float m_fRotationSpeed = 1.5f;
    private float m_fRotationValue;

    // Gets called every frame
    private void Update()
    {
        m_fRotationValue += m_fRotationSpeed * Time.deltaTime;
        RenderSettings.skybox.SetFloat("_Rotation", m_fRotationValue);
    }
}

```

# Query ID - TS0002

## Category
T-Sharp Scripting

## Query Text
How do I change the emission color of a tile when the player touches it, resetting it to black at the start? 

## Expected Answer
The code below helps you do that. The Start() function first resets the emission Color to Black at the beginning of the game. The OnTriggerEnter function then detects if the player has touched the tile through the StudioController wrapper and changes the colour 

### Code
```csharp

using System;
using System.Collections;
using Terra.Studio;
using Terra.Studio.Exposed;
using Terra.Studio.Exposed.Layers;
using UnityEngine;

public class TileColorChanger : StudioBehaviour
{
    private Color m_refEmissionColor;
    private bool m_bColorHasChanged;
    // Gets called at the start of the lifecycle of the GameObject
    private void Start()
    {
        m_refEmissionColor = (this.gameObject.GetComponent(typeof(Renderer)) as Renderer).material.GetColor("_EmissionColor");
        m_bColorHasChanged = false;
        (this.gameObject.GetComponent(typeof(Renderer)) as Renderer).material.SetColor("_EmissionColor", Color.black);
    }

    void OnTriggerEnter(Collider col)
    {
        if (!m_bColorHasChanged && StudioController.CheckIfController(col.gameObject) != null && m_refEmissionColor != null)
        {
            (this.gameObject.GetComponent(typeof(Renderer)) as Renderer).material.SetColor("_EmissionColor", m_refEmissionColor);
            m_bColorHasChanged = true;
        }
    }
}

```

## Difficulty
Medium 

## Keywords/Tags
#emissioncolorchange #materialchange



