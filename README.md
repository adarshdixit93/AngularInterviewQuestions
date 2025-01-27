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

----------
### Q3. Angular mein Directives kya hote hain?
Directives aise attributes hote hain jo users ko apne applications ke liye new HTML syntax likhne ki suvidha dete hain. Jab bhi Angular compiler DOM mein kisi directive ko find karta hai, wo execute hota hai. Angular mein teen types ke directives hote hain:

1. Component Directives
Component directives wo directives hote hain jo ek complete Angular component ko define karte hain. Yeh basically ek Angular component ke functionality ko DOM mein render karne ke liye kaam aate hain. Component directives ke paas ek template hota hai jisme logic aur view (HTML) dono hote hain. Inhe hum @Component decorator ke saath define karte hain.

Example:

```typescript
@Component({
  selector: 'app-header',  // This is a component directive
  templateUrl: './header.component.html',
  styleUrls: ['./header.component.css']
})
export class HeaderComponent {
  title = 'My Application Header';
}
```
Yahaan `@Component` directive ko use karke HeaderComponent ko define kiya gaya hai. Is component ka apna ek template aur logic hota hai, jo Angular DOM mein render hoga jab `<app-header></app-header>` tag use hoga.

2. Structural Directives
Structural directives woh directives hote hain jo DOM ko change karte hain, yani wo elements ko add ya remove karte hain. Ye directives DOM ka structure modify karte hain, jise hum ` * ` se represent karte hain. Yeh conditional rendering aur loops jaise features ko implement karne mein kaam aate hain.

Common Examples:

`*ngIf:` Ye directive kisi element ko condition ke basis par render karta hai.
*ngFor:` Ye directive kisi list ko iterate karne ke liye use hota hai.
Example:

```html
<div *ngIf="isLoggedIn">Welcome, User!</div>
```
Yahaan `*ngIf` structural directive hai jo condition ke according Welcome, User! ko display karega. Agar isLoggedIn variable true hoga, tab ye div display hoga, warna nahi.

```html
<ul>
  <li *ngFor="let item of items">{{ item }}</li>
</ul>
```
Is example mein `*ngFor` directive items array ke har item ke liye ek `<li>` element banata hai. Har item ko dynamically HTML mein render kiya jata hai.

3. Attribute Directives
Attribute directives wo directives hote hain jo kisi element ka behavior ya appearance modify karte hain bina uske structure ko change kiye. Ye directives element ke style, classes, ya attributes ko modify karne ke liye use hote hain.

Common Examples:

`ngClass:` Ye directive kisi element ke class ko dynamically add/remove karta hai.
`ngStyle:` Ye directive kisi element ke inline styles ko dynamically change karta hai.
`ngModel:` Ye directive form inputs ko bind karta hai.
Example:

```html
<button [ngClass]="{'btn-primary': isPrimary}">Click me</button>
```
Yahaan `ngClass` attribute directive hai jo button ki class ko dynamically set karta hai. Agar isPrimary true hai, toh button ko btn-primary class milegi.

```html
<div [ngStyle]="{'color': fontColor}">This text has dynamic color!</div>
```
Is example mein `ngStyle` directive ko use karke text ke color ko dynamically change kiya gaya hai. fontColor variable se color set hota hai.

*** Summary:
Component Directives: Ye ek complete component ko define karte hain jisme logic aur view dono hote hain.
Structural Directives: Ye DOM structure ko modify karte hain, jaise element ko show ya hide karna ya loops ko handle karna.
Attribute Directives: Ye kisi element ke behavior ya appearance ko modify karte hain, bina uske structure ko badle.
In directives ka main kaam Angular ke HTML ko dynamic aur interactive banana hota hai. Wo application ke logic aur views ko Angular ke DOM mein achhe se integrate karte hain, jisse ki hum apne UI ko dynamically modify kar sakein.***
---------------
