C# MONOBEHAVIOUR
// Concept: A game character represented as data + behavior(a class).
// CODE PROPER
using System;
class character 
{

		public string Name;
		public int X, Y;. //position on the map
		public int Width, Height; //bounding shape
		public int Health;

		// Constructor: how a chatacter is "born"
		public Character "string name, int x, int y, int width, in height, int health"

		{
			Name = name ;
			X = x;
			Y = y;
			Width =width
			Height = height;
			Health = health;

	//Behavior: methods define what the character can Do
	public void MoveTo(int newX, int newY)
	{
	 X =newX;
	 Y =newY;
	 Console.Writeline($"{Name} moved to ({X}),{Y})");
	}
	public void TakenDamage(int amount)
	{
	 Health -= amount; // Decreased of your health
	 Health = Math.Max(Health , 0);
	 Console.Writeline("{Name} tool {amount} damage.Health:{Health}");
	}the character as an ASCII rectangle
	   for (int row = 0; < Height' row++)
	   {
		Console.Writeline(new string('#', Width));
	   }
	}
}

//Movement for Gridbased Character
class Program
{
	static void Main()
	{
		Character hero = new Character("Hero", 0, 0, 3, 2, 100);
		hero:PrintShape();
		hero:MoveTo(5 , 3);
		hero.TakeDamage(25);

	}
}
// GRID BASE Movement
// GameObject
using UnityEngine;
public class GridMovement : MONOBEHAVIOUR
{
		public float tileSize=1,0f; // size of one grid cell
		public float moveSpeed = 10f // how fast we glide between tile(feel, not logic)
		public Vector3 targetPositionl
		private bool isMoving = false;

		void Start()
		{
		  // Snap starting position to the grid so everything lines up
        targetPosition = SnapToGrid(transform.position);
		transform.position =targetPosition
		}
		void Update()
		}
		  if(!isMoving)'
		  {
			hadleInput();
		  }
		  else
		{
			//smoothly guid to the next lines
		  transform.position=Vector3. MoveWards(transform.position,targetPosition.moveSpeed * Tile.deltaTime);
		if (Vector 3.Distance(transform.position,targetPositionl) <0.001f)
		{
			transform.position = targetPosition;
			isMoving = false;
		}
	}
}

 void HandleInput()

{
	Vector3 direction = Vector3.zero;

	if(Input.GetKeyDown(KeyCode.W)) direction = Vector3.up;
	else if(Input.GetKeyDown(KeyCode.S)) direction =Vector3.down;
	else if(Input.GetKeyDown(KeyCode.A)) direction =Vector3.left;
	else if(Input.GetKeyDown(KeyCode.D)) direction =Vector3.right;

	if (direction != Vector3.zero)
	{
		targetPosition =transform.position + direction * tileSize;
		isMoving =true;
	{
	return new Vector3(
		Mathf.Round(pos.x / tileSize) *tileSize,
		Mathf.Rount(pos.y / tileSize) *tileSize,
		pos.z
	);

  }  
}
//Movement for freemovement(VECTOR BASEED) Character
using UnityEngine;
public class FreeMovement: MonoBehaviour
{
		public float moveSpeed 5f;

		void update()
		{
		 // GetAxis give smooth values between -1 and 1
		 float horizontal =Input.GetAxis("Horizontal"); // A/D pr LEFT/RIGHT ARROWS
		 float vertical =Input.GetAxis("Vertical"); // W/S or UP/DOWN ARROWS
		 Vector3 direction =new Vector3(horizontal, vertical, 0f);
		 // Diagonal Movementif(direction.magnitude > 1f)
		 {
			direction.Normalize();
		}
			transform.position += direction * moveSpeed * Time.deltaTime;
		}
	}


//Movement for Physicsbased Character
// GameObject/ Rigibody2D component
using UnityEngine;

[RequireComponent(typeif(Rigibody2D))]
public class PhysicsMovement: MonoBehaviour
{
		public float mobeForce =10f;
		public float jumpForce = 7f;
		public float maxSpeed = 6f;

		private Rigidbody2D rb;
		private blood isGrounded = false;

		void Start()
		{
				rb = GetComponent<Rigidbody2D>();
		}
		void FixedUpdate()
		{
		//Physic change FixedUpdate
		// frame rectanglefloat horizontal= Input.GetAxis("Horizontal");
		rb.AddForce(new Vector2(horizontal * moveForce, 0f));
		// Clam Horizontal
		if(Mathf.Abs(rb.velocity.x)> maxSpeed)
		{
				rb.velocity = new Vector2(Mathf.Sign(rb.velocity.x)* maxSpeed, rb.velocity.y);
		}
	}
		void OnCollisonEnter2D(Collison2D collison)
		{
				if (collison.gameObject.CompareTag("Ground"))
				{
					isGrounded =true;
				}
		}
		void OnCollisonExit2D(Collison2D collison)
		{
				if(collison.gameObject.CompareTag("Ground"))
				{
					is Ground = false;
				}
	public void PrintShape()
	{
	  //Draw 
		}
}
