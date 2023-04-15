# PhotoFrameApp

App : When you click on the next button you will see the more images and when you click on the previous button you will see the previous images.

Code for MainActivity in the project is :

    import android.widget.TextView

    class MainActivity : AppCompatActivity() {

    var currentImage = 0

    val names = arrayOf("GAME CHANGER","PUSHPA 2" , "SALAAR" , "SSMB28" )

    lateinit var image : ImageView

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        supportActionBar?.hide()

        val prev = findViewById<ImageButton>(R.id.imgPrev)
        val next = findViewById<ImageButton>(R.id.imgNext)
        val text = findViewById<TextView>(R.id.textView)

        prev.setOnClickListener{
            val idCurrentImageString = "pic$currentImage"
            //convert string id into integer address associated with it
            val idCurrentImageInt = this.resources.getIdentifier(idCurrentImageString, "id",packageName)
            image = findViewById(idCurrentImageInt)
            image.alpha= 0f

            currentImage = (4+currentImage-1)%4

            val idImageToShowString = "pic$currentImage"
            //convert string id into integer address associated with it
            val idImageToShowInt = this.resources.getIdentifier(idImageToShowString, "id",packageName)
            image = findViewById(idImageToShowInt)
            image.alpha= 1f

            //text
            text.text = names[currentImage]


        }

        next.setOnClickListener {
            val idCurrentImageString = "pic$currentImage"
            //convert string id into integer address associated with it
            val idCurrentImageInt = this.resources.getIdentifier(idCurrentImageString, "id",packageName)
            image = findViewById(idCurrentImageInt)
            image.alpha= 0f

            currentImage = (4+currentImage+1)%4

            val idImageToShowString = "pic$currentImage"
            //convert string id into integer address associated with it
            val idImageToShowInt = this.resources.getIdentifier(idImageToShowString, "id",packageName)
            image = findViewById(idImageToShowInt)
            image.alpha= 1f
            text.text = names[currentImage]

        }

        }
    }
