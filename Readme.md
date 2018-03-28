## Android-TPCalculatriceSimple

### Visualisation
![Image](https://imghost.io/images/2018/03/28/Calc.jpg)

### Code de Calcule Java (class home)
```markdown 

import android.os.Bundle;
import android.app.Activity;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;

public class home extends Activity {
    //declaration de la zone de saisie
    EditText num;

    //declaration des boutton
    Button button;
    Button button1;
    Button button2;
    Button button3;
    Button button4;
    Button button5;
    Button button6;
    Button button7;
    Button button8;
    Button button9;

    //button action
    Button buttonPlus;
    Button buttonMoins;
    Button buttonDiv;
    Button buttonMul;
    Button buttonclearResultat;
    Button buttonEgal;
    Button buttonPoint;

    private double res;
    private boolean OPERATION = false;
    private String OPERATEUR = "";
    private boolean update = false;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_home); 

        //accesse au variables
        num = (EditText) findViewById(R.id.result);
        button = (Button) findViewById(R.id.Zero);
        button1 = (Button) findViewById(R.id.un);
        button2 = (Button) findViewById(R.id.deux);
        button3 = (Button) findViewById(R.id.trois);
        button4 = (Button) findViewById(R.id.quatre);
        button5 = (Button) findViewById(R.id.cinq);
        button6 = (Button) findViewById(R.id.six);
        button7 = (Button) findViewById(R.id.sept);
        button8 = (Button) findViewById(R.id.huit);
        button9 = (Button) findViewById(R.id.neuf);
        buttonPlus =(Button) findViewById(R.id.plus);
        buttonMoins = (Button) findViewById(R.id.moin);
        buttonMul = (Button) findViewById(R.id.multi);
        buttonDiv = (Button) findViewById(R.id.divis);
        buttonPoint = (Button) findViewById(R.id.point);
        buttonEgal = (Button) findViewById(R.id.calc);
        buttonclearResultat= (Button) findViewById(R.id.clear);


        // Ecoute des boutton
        button.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                CorrespandanceAjout("0");
            }
        });

        button1.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                CorrespandanceAjout("1");
            }
        });

        button2.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                CorrespandanceAjout("2");
            }
        });

        button3.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                CorrespandanceAjout("3");
            }
        });

        button4.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                CorrespandanceAjout("4");
            }
        });

        button5.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                CorrespandanceAjout("5");
            }
        });

        button6.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                CorrespandanceAjout("6");
            }
        });

        button7.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                CorrespandanceAjout("7");
            }
        });

        button8.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                CorrespandanceAjout("8");
            }
        });

        button9.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                CorrespandanceAjout("9");
            }
        });

        buttonPlus.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                //CorrespandanceAjout("+");
                plusClick();

            }
        });

        buttonMoins.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                moinsClick();
            }
        });

        buttonMul.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                mulClick();
            }
        });

        buttonDiv.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                divClick();
            }
        });

        buttonEgal.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                ResultatAF();
            }
        });

        buttonPoint.setOnClickListener(new View.OnClickListener() {
            public void onClick(View v) {
                CorrespandanceAjout(".");
            }
        });

        buttonclearResultat.setOnClickListener(new View.OnClickListener(){
            public void onClick(View v){
                clearResultatClick();
            }
        });


    }

    //Retoune le chiffre
    public void CorrespandanceAjout(String str) {
        if(update){
            update = false;
        }else{
            if(!num.getText().equals("0"))
                str = num.getText() + str;
        }
        num.setText(str);
    }


    //Addition
    public void plusClick(){
        //si OPERATION est vrai on calcule sinon on renvoi le resultat
        if(OPERATION){
            calcul();
            num.setText(String.valueOf(res));
        }else{
            res = Double.valueOf(num.getText().toString()).doubleValue();
            OPERATION = true;
        }
        OPERATEUR = "+";
        update = true;
    }

    //Soustraction
    public void moinsClick(){
        if(OPERATION){
            calcul();
            num.setText(String.valueOf(res));
        }else{
            res = Double.valueOf(num.getText().toString()).doubleValue();
            OPERATION = true;
        }
        OPERATEUR = "-";
        update = true;
    }


    //Multiplication
    public void mulClick(){
        if(OPERATION){
            calcul();
            num.setText(String.valueOf(res));
        }else{
            res = Double.valueOf(num.getText().toString()).doubleValue();
            OPERATION = true;
        }
        OPERATEUR = "*";
        update = true;
    }

    //division
    public void divClick(){
        if(OPERATION){
            calcul();
            num.setText(String.valueOf(res));
        }else{
            res = Double.valueOf(num.getText().toString()).doubleValue();
            OPERATION = true;
        }
        OPERATEUR = "/";
        update = true;
    }

    //Résultat
    public void ResultatAF(){
        calcul();
        update = true;
        OPERATION = false;
    }

    //clearResultat
    public void clearResultatClick() {
        OPERATION = false;
        update = true;
        res = 0;
        OPERATEUR = "";
        num.setText("");

    } 

    //Fait le calcul
    private void calcul(){
        if(OPERATEUR.equals("+")){
            res = res + Double.valueOf(num.getText().toString()).doubleValue();
            num.setText(String.valueOf(res));
        }

        if(OPERATEUR.equals("-")){
            res = res - Double.valueOf(num.getText().toString()).doubleValue();
            num.setText(String.valueOf(res));
        }

        if(OPERATEUR.equals("*")){
            res = res * Double.valueOf(num.getText().toString()).doubleValue();
            num.setText(String.valueOf(res));
        }

        if(OPERATEUR.equals("/")){
            try{
                res = res / Double.valueOf(num.getText().toString()).doubleValue();
                num.setText(String.valueOf(res));
            }catch(ArithmeticException e){
                num.setText("0");
            }
        }
    }


}
```

### Licence MIT
### Support or Contact https://www.linkedin.com/in/mohamedharir/
