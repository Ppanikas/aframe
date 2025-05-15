using UnityEngine;
using UnityEngine.XR.Interaction.Toolkit;
using UnityEngine.InputSystem;

[RequireComponent(typeof(Rigidbody))]
public class CarController : MonoBehaviour
{
    [Header("Wheel Colliders")]
    public WheelCollider wcFL, wcFR, wcRL, wcRR;

    [Header("Wheel Meshes")]
    public Transform meshFL, meshFR, meshRL, meshRR;

    [Header("Car Settings")]
    public float maxMotorTorque = 1500f;    // δύναμη κινητήρα
    public float maxSteeringAngle = 30f;    // γωνία τιμονιού

    private float motorInput = 0f;
    private float steerInput = 0f;

    // Input Actions (νέο Input System)
    public InputActionProperty throttleAction;
    public InputActionProperty steerAction;

    void FixedUpdate()
    {
        // Ανάγνωση αξόνων
        motorInput = throttleAction.action.ReadValue<float>();
        steerInput = steerAction.action.ReadValue<float>();

        // Εφαρμογή κινητήρα
        wcFL.motorTorque = maxMotorTorque * motorInput;
        wcFR.motorTorque = maxMotorTorque * motorInput;
        wcRL.motorTorque = maxMotorTorque * motorInput;
        wcRR.motorTorque = maxMotorTorque * motorInput;

        // Εφαρμογή τιμονιού (μόνο εμπρός τροχοί)
        float steerAngle = maxSteeringAngle * steerInput;
        wcFL.steerAngle = steerAngle;
        wcFR.steerAngle = steerAngle;

        // Αναπαράσταση τροχών (οπτικά)
        UpdateWheelPose(wcFL, meshFL);
        UpdateWheelPose(wcFR, meshFR);
        UpdateWheelPose(wcRL, meshRL);
        UpdateWheelPose(wcRR, meshRR);
    }

    void UpdateWheelPose(WheelCollider wc, Transform mesh)
    {
        Vector3 pos; Quaternion rot;
        wc.GetWorldPose(out pos, out rot);
        mesh.position = pos;
        mesh.rotation = rot;
    }
}

