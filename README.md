# KIGapp
public 
app/
gradle/
build.gradle
settings.gradle
codemagic.yamlpackage com.example.kigapp

import android.os.Bundle
import androidx.activity.ComponentActivity
import androidx.activity.compose.setContent
import androidx.compose.foundation.background
import androidx.compose.foundation.layout.*
import androidx.compose.foundation.shape.RoundedCornerShape
import androidx.compose.material.icons.Icons
import androidx.compose.material.icons.filled.Check
import androidx.compose.material.icons.filled.Warning
import androidx.compose.material3.*
import androidx.compose.runtime.Composable
import androidx.compose.ui.Alignment
import androidx.compose.ui.Modifier
import androidx.compose.ui.graphics.Color
import androidx.compose.ui.text.font.FontWeight
import androidx.compose.ui.unit.dp
import androidx.compose.ui.unit.sp

class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent { HomeScreen() }
    }
}

@Composable
fun HomeScreen() {
    Column(
        modifier = Modifier
            .fillMaxSize()
            .background(Color(0xFFEAF6F4))
            .padding(16.dp)
    ) {
        Text("КИГ: AB0091405", fontWeight = FontWeight.Bold, fontSize = 20.sp)
        Spacer(modifier = Modifier.height(16.dp))
        StatusCard("Геолокация", "Передана", true)
        StatusCard("Аутентификация", "Пройдена", true)
        StatusCard("Постановка на учет", "Вы сняты", false)
    }
}

@Composable
fun StatusCard(title: String, status: String, ok: Boolean) {
    Card(
        modifier = Modifier.fillMaxWidth().padding(vertical = 6.dp),
        shape = RoundedCornerShape(16.dp)
    ) {
        Row(
            modifier = Modifier.padding(16.dp),
            verticalAlignment = Alignment.CenterVertically
        ) {
            Column(modifier = Modifier.weight(1f)) {
                Text(title, fontWeight = FontWeight.SemiBold)
                Text(status)
            }
            Icon(
                imageVector = if (ok) Icons.Default.Check else Icons.Default.Warning,
                contentDescription = null,
                tint = if (ok) Color(0xFF2E7D32) else Color.Red
            )
        }
    }
}
