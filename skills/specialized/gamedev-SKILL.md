---
name: gamedev
description: Game development skill - Unity, Unreal, Godot, graphics, physics
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [develop, optimize, design, debug, deploy] }
    engine: { type: string, enum: [unity, unreal, godot, custom] }
  required: [task]

output_schema:
  type: object
  properties:
    code: { type: string }
    architecture: { type: string }
    performance_metrics: { type: object }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 60000
---

# Game Development Skill

## PURPOSE
Game development with major engines, graphics programming, and optimization.

## CORE COMPETENCIES
```
Game Engines:
├── Unity (C#)
├── Unreal Engine (C++/Blueprints)
├── Godot (GDScript/C#)
└── Custom engines

Graphics:
├── Shaders (HLSL/GLSL)
├── Rendering pipelines
├── Lighting systems
├── Particle effects
└── Post-processing

Systems:
├── Physics simulation
├── AI/Pathfinding
├── Networking/Multiplayer
├── Audio systems
└── Save/Load systems
```

## CODE PATTERNS

### Unity Component
```csharp
using UnityEngine;
using System.Collections;

public class PlayerController : MonoBehaviour
{
    [SerializeField] private float moveSpeed = 5f;
    [SerializeField] private float jumpForce = 10f;

    private Rigidbody2D rb;
    private bool isGrounded;

    private void Awake()
    {
        rb = GetComponent<Rigidbody2D>();
    }

    private void Update()
    {
        float horizontal = Input.GetAxisRaw("Horizontal");
        rb.velocity = new Vector2(horizontal * moveSpeed, rb.velocity.y);

        if (Input.GetButtonDown("Jump") && isGrounded)
        {
            rb.AddForce(Vector2.up * jumpForce, ForceMode2D.Impulse);
        }
    }

    private void OnCollisionEnter2D(Collision2D collision)
    {
        if (collision.gameObject.CompareTag("Ground"))
            isGrounded = true;
    }
}
```

### Unreal Actor
```cpp
// PlayerCharacter.h
UCLASS()
class APlayerCharacter : public ACharacter
{
    GENERATED_BODY()

public:
    APlayerCharacter();

    UPROPERTY(EditAnywhere, BlueprintReadWrite, Category = "Movement")
    float MoveSpeed = 600.0f;

protected:
    virtual void BeginPlay() override;
    virtual void Tick(float DeltaTime) override;
    virtual void SetupPlayerInputComponent(UInputComponent* InputComponent) override;

private:
    void MoveForward(float Value);
    void MoveRight(float Value);
};
```

### Shader Example
```hlsl
Shader "Custom/ToonShader"
{
    Properties
    {
        _MainTex ("Texture", 2D) = "white" {}
        _RampTex ("Ramp", 2D) = "white" {}
    }

    SubShader
    {
        Pass
        {
            CGPROGRAM
            #pragma vertex vert
            #pragma fragment frag

            float4 frag(v2f i) : SV_Target
            {
                float NdotL = dot(i.normal, _WorldSpaceLightPos0.xyz);
                float ramp = tex2D(_RampTex, float2(NdotL * 0.5 + 0.5, 0.5)).r;
                return tex2D(_MainTex, i.uv) * ramp;
            }
            ENDCG
        }
    }
}
```

## PERFORMANCE OPTIMIZATION
```
CPU:
├── Object pooling
├── LOD systems
├── Culling strategies
├── Job system / threading
└── Data-oriented design

GPU:
├── Batching (static/dynamic)
├── Texture atlasing
├── Shader optimization
├── Occlusion culling
└── GPU instancing

Memory:
├── Asset streaming
├── Garbage collection management
├── Addressables
└── Memory profiling
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| Low FPS | Draw calls | Batching, atlasing |
| Stuttering | GC spikes | Object pooling |
| Memory leak | Unreleased refs | Proper cleanup |
| Physics jitter | Variable timestep | FixedUpdate |
