<uses-permission android:name="android.permission.READ_PHONE_STATE" />
<uses-permission android:name="android.permission.RECEIVE_SMS" />
import android.Manifest
import android.content.pm.PackageManager
import android.os.Bundle
import android.telephony.TelephonyManager
import android.widget.Toast
import androidx.appcompat.app.AppCompatActivity
import androidx.core.app.ActivityCompat

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        if (ActivityCompat.checkSelfPermission(this, Manifest.permission.READ_PHONE_STATE) != PackageManager.PERMISSION_GRANTED) {
            ActivityCompat.requestPermissions(this, arrayOf(Manifest.permission.READ_PHONE_STATE), 1)
        } else {
            showContactInfo()
        }
    }

    private fun showContactInfo() {
        val phoneNumber = getIncomingPhoneNumber() // Implémentez la méthode pour obtenir le numéro
        // Afficher vos coordonnées ou votre activité ici
        Toast.makeText(this, "Mes coordonnées : votre-email@example.com\nActivités : Développeur, Consultant", Toast.LENGTH_LONG).show()
    }

    // Implémentez ici la logique pour récupérer le numéro de téléphone entrant
}
<receiver android:name=".CallReceiver">
    <intent-filter>
        <action android:name="android.intent.action.PHONE_STATE" />
    </intent-filter>
</receiver>


