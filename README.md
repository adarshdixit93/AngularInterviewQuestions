# AngularInterviewQuestions
-------------
### Q1.Data binding kya hota hai? Angular kaunsa data binding use karta hai?

Data binding ek phenomenon hai jo internet users ko Web browser ke madhyam se Web page elements ko manipulate karne ki suvidha deta hai. Isme dynamic HTML ka use hota hai aur complex scripting ya programming ki zarurat nahi hoti. Data binding ka istemal un web pages mein hota hai jo interactive components jaise forms, calculators, tutorials, aur games contain karte hain. Jab web pages mein data kaafi zyada hota hai, tab incremental display ki wajah se data binding kaafi convenient ho jata hai.  
**Angular two-way binding ka use karta hai.**  
Isme agar user interface mein koi change hota hai, toh woh model state mein reflect hota hai. Aur agar model state mein koi change hota hai, toh woh UI state mein bhi dikhai deta hai. Ye framework DOM ko Model data ke saath connect karne ke liye controller ka use karta hai. Lekin ye approach performance ko impact kar sakti hai, kyunki har DOM change ko track karna padta hai.

----------
### Q2. Angular mein decorators kya hote hain?  
Decorators ek design pattern ya function hote hain jo Angular ki features ko define karte hain. Ye kisi class, service, ya filter ko pehle se modify karne ke liye use kiye jaate hain. Angular mein chaar types ke decorators hote hain, jo hain:

1. **Class Decorators**  
Class decorators ko hum kisi class ko define karne ke liye use karte hain. Ye decorators class ko Angular ke context mein ek specific role de dete hain, jaise ki service, component, directive, etc. For example, `@Component`, `@Injectable` aur `@NgModule` sab class decorators hain. Inka kaam class ko define karna hota hai ki woh kis type ka component hai, ya kis cheez ki service provide kar raha hai.  
**Example:**  
```typescript
@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent { }
```
Yahaan `@Component` ek class decorator hai jo `AppComponent` class ko ek Angular component banata hai.

2. **Property Decorators**  
Property decorators ko hum kisi class ki properties ko annotate karne ke liye use karte hain. Ye decorators Angular ko batate hain ki kis property ko kisi specific functionality ki zarurat hai, jaise ki dependency injection. Inka use class ki fields ya properties mein hota hai.  
**Example:**  
```typescript
export class AppComponent {
  @Input() name: string; // @Input is a property decorator
}
```
Yahaan `@Input` property decorator hai jo `name` ko parent component se data pass karne ke liye allow karta hai.

3. **Method Decorators**  
Method decorators ko hum kisi class ke methods ko modify karne ke liye use karte hain. Inka use methods ko special functionality dene ke liye hota hai, jaise ki lifecycle hooks, event handlers, etc. Yeh decorators method ko Angular ke lifecycle mein integrate karte hain.  
**Example:**  
```typescript
@Injectable({
  providedIn: 'root',
})
export class MyService {
  constructor() {}
  
  @HostListener('click', ['$event'])  
  onClick(event: MouseEvent) {   // @HostListener is a method decorator
    console.log(event);
  }
}
```
Yahaan `@HostListener` ek method decorator hai jo component ko kisi event listener se connect karta hai, jaise click event ko handle karne ke liye.

4. **Parameter Decorators**  
Parameter decorators ko hum methods ke parameters ko modify karne ke liye use karte hain. Ye decorators Angular ko batate hain ki method ke parameters ko kis tarah se inject ya treat karna hai. Inka use mostly dependency injection mein hota hai.  
**Example:**  
```typescript
constructor(@Inject(LOCALE_ID) public locale: string) { }
```
Yahaan `@Inject` ek parameter decorator hai jo `locale` parameter ko inject karta hai aur Angular ko batata hai ki `LOCALE_ID` ke value ko pass kiya jaye.

In sab decorators ka major role Angular ke features ko customize karna aur Angular ko bataana hota hai ki kis class, method, ya property ka kya role hai, taki Angular unko sahi tareeke se handle kar sake. Ye decorators Angular ke internal framework ko inform karte hain aur application ke behavior ko modify karne mein madad karte hain.
