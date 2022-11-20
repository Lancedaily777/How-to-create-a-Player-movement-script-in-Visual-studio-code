# How-to-create-a-Player-movement-script-in-Visual-studio-code
Hello! Copy and paste OR study what im about to show you which is a file saying the code
//Here is the script




using System.Collections;
using UnityEngine;


public class PlayerMovement : MonoBehavior
{

    private float horizontal;
    private float speed = 8f;
    private float jumpingPower = 16f;
    private bool IsFacingRight = true;

    [SerializeField] private RigidBody2D rb;
    [SerializeField] private Transform groundCheck;
    [SerializeField] private LayerMask groundLayer;

    // Update is called once per frame
    void Update()
    {
       horizontal = Input.GetAxisRaw("Horizontal");

       if (Input.GetButtonDown("Jump") && IsGrounded())
       {
        rb.velocity = new Vector2 = new Vector2(rb.velocity.x, jumpingPower);
       }

       if (Input.GetButtonUp("Jump") && rb.velocity.y > 0f)
       {
        rb.velocity = new Vector2(rb.velocity.x rb.velocity.y * 0.5f);
       }

       Flip();
    }


    private void FixedUpdate()
    {
       rb.velocity = new Vector2(horizontal * speed, rb.velocity.y)
    }

    private bool IsGrounded()
    {
        return Physics2D.OverlapCircle(groundCheck.Position, 0.2f, groundLayer);
    }

    private void Flip()
    {
        if (IsFacingRight && horizontal < 0f || !IsFacingRight && horizontal > 0f)
        {
            IsFacingRight = !IsFacingRight;
            Vector3 localScale = transform.localScale;
            localScale.x *= -1f;
            transform.localScale = localScale;
        }
    }
}
