Android skaiciuotuvo kodas
==================

package com.example.skaiciuotuvas;

import android.os.Bundle;
import android.app.Activity;
import android.view.Menu;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;

public class MainActivity extends Activity {
	TextView Disp;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        Disp=(TextView)findViewById(R.id.textView1);
        Disp.setText("0");
    }


    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.main, menu);
        return true;
    }
    static boolean isemty=true;
    public void num_Clicked(View sender)
    {
    	Button bt=(Button)sender;
    	if(Disp.getText().length()>7)return;
    	if(isemty)
    	{
    		if(bt.getText().toString().equals("0"))return;
    		Disp.setText(bt.getText());	
    		isemty=false;
    	}
    	else
    	{
        	Disp.append(bt.getText());	
    	}
    }
    static Integer accumulator=0;
    static short operationToDo=0;
    public void op_Clicked(View sender)
    {
    	Button bt=(Button)sender;
    	switch (operationToDo)
    	{
    	case 0:
    		accumulator+=Integer.parseInt(Disp.getText().toString());
    	case 1:
    		accumulator-=Integer.parseInt(Disp.getText().toString());
    	break;
    	}
    	Disp.setText(Float.toString(accumulator));
    	if(bt.getText().toString().equals("+")) operationToDo=0;
    	if(bt.getText().toString().equals("-")) operationToDo=1;
    	isemty=true;
    	}
    }
    
