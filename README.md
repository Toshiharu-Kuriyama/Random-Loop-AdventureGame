# Random-Loop-AdventureGame

#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

int main() {
  
  srand(static_cast<unsigned int>(time(0)));
  int randomNumber = rand();
  int number = (10 +randomNumber % 80) + 1;
  int firstNumber = (-5 + randomNumber % 10) + number;
  int secondNumber = (-10 + randomNumber % 5) + number;
  int thirdNumber = (1+randomNumber % 5) + number;
  int fourNumber = (-5 + randomNumber % 5) + number;
  int fiveNumber = (-2 + randomNumber % 3) + number;
  int count = 0;
  int calcNumber;

  if(firstNumber >= number || firstNumber <= number)
  {
    firstNumber += 1;
  }
  
  if(thirdNumber >= number)
  {
    thirdNumber += 1;
  }
  if(thirdNumber >= firstNumber){
    thirdNumber += 1;
  }
  if(thirdNumber >= fiveNumber){
    thirdNumber += 1;
  }
  
  if(fourNumber <= number)
  {
    fourNumber -= 1;
  }
  if(fourNumber >= firstNumber){
    fourNumber += 1;
  }

  if(fiveNumber >= number)
  {
    fiveNumber += 1;
  }
  if(fiveNumber <= number)
  {
    fiveNumber -= 1;
  }
  if(fiveNumber >= thirdNumber)
  {
    fiveNumber += 1;
  }
  if(fiveNumber >= fourNumber)
  {
    fiveNumber += 1;
  }
  
  cout<<"＜System＞ようこそ審判の間へ！\n";
  cout<<"＜System＞唐突ですが、あなたは死にました。\n";
  cout<<"＜System＞天国に行くか地獄に行くか、ゲームの成否によって決めていただきます。\n";
  cout<<"＜System＞ゲームは簡単！先人たちが残した手掛かりを元に、1~100までの中から1つ選ばれた数字を当てて下さい。\n";
  cout<<"＜System＞回答は3回までとなります。それではゲームスタートです！\n\n";
  
  int answer;
  do
  {
    cout<<"\n---先人たちの手掛かり---\n";
    cout<<"正解の数字に近かった5人の数字は以下の通り\n";
    cout<<"１人目の数字は"<<firstNumber<<"。\n";
    cout<<"２人目の数字は"<<secondNumber<<"。\n";
    cout<<"３人目の数字は"<<thirdNumber<<"。\n";
    cout<<"４人目の数字は"<<fourNumber<<"。\n";
    cout<<"５人目の数字は"<<fiveNumber<<"。\n";
    
    if(count == 2)
    {
      cout<<"\n我々は最後にヒントを託す...。\n";
      cout<<"入力した数字が選ばれた数字に近ければ、文章が変わる。\n";
      cout<<"1つだけずれていると「惜しい」と出る。\n";
      cout<<"2つであれば「付近に正解がある」と出る。\n";
      cout<<"3つであれば「もう少しずれたら当たる」と出る。\n";
      cout<<"それ以上ずれると「見事に外れました」としか出ない。\n";
      cout<<"以上のことを踏まえて正解を導き出してくれ。幸運を祈る！\n";
    }
      
    
    count++;

    switch(count)
    {
      case 1:cout<<"\n＜System＞当たれば天国、外れれば地獄の推測ゲーム!!　運命の1答目は...。\n\n";
      break;
      case 2:cout<<"\n＜System＞あと残りは2回...。次の回答で成功となるか!?　運命の2答目は...。\n\n";
      break;
      case 3:cout<<"\n＜System＞残すところあと1回となりました。もう間違えることはできない!　天国へ行けるか、はたまた地獄へ落ちるか　運命の3答目は...。\n\n";
      break;
    }
    
    cout<<"＜System＞数字を入力してください: ";
    cin>>answer;

    calcNumber = number - answer;
    if(calcNumber < 0)
    {
      calcNumber = -(number - answer);
    }

    if(count < 3)
    {
      switch(calcNumber)
      {
        case 0:
        break;
        case 1:cout<<"\n＜System＞外れてしまいましたが、惜しいですね。\n";
        break;
        case 2:cout<<"\n＜System＞外れました。しかし、案外その付近の数字に正解があるかもしれないですね？\n";
        break;
        case 3:cout<<"\n＜System＞外れです。ですが、もう少しずれていたら当たっていたかもしれないですね？\n";
        break;
        default:cout<<"\n＜System＞見事に外れましたね。\n";
        break;
      }
    }
    else if(count == 3 && answer != number)
    {
      cout<<"\n＜System＞正解とはならず！\n";
    }
    
    if(count == 3)
      break;
    
  }while(answer != number);

  if(count == 3 && answer != number)
  {
    cout<<"\nそして3回とも不正解だったので、地獄行きが確定しました!\n";
    cout<<"ちなみに、"<<number<<"が正解の数字でした。残念!!";
  }else{
    cout<<"\n＜System＞Congratulations!\n";
  cout<<"＜System＞見事!正解の数字を当てたあなたは、ゲームクリアとなりますので天国へと向かっていただきます。\n";
  cout<<"＜System＞それではいってらっしゃいませ～!\n";
  }
}