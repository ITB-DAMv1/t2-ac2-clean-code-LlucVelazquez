# Clean Code

**Lluc Velázquez**

## Chapter 1:

You might argue that a book about code is obsolete, that code is no longer the problem, and that we should focus on models and requirements.
Some suggest that the end of code is near. That programmers will no longer be needed because business people will generate programs from specifications.

This is not true. Code will never go away, because it represents the details of requirements. At some level, those details cannot be ignored or abstracted away; they must be specified, and to specify requirements in a way that a team can execute them, programming is needed. That specification is code.

If you've been a programmer for two or three years, you've probably suffered from the disasters committed by others in the code. If you're more experienced, you've suffered to a greater extent. The degree of suffering can be significant.

It may be hard to hear. How can we possibly be responsible for such disasters? What about requirements? What about deadlines? What about incompetent managers and pointless salespeople?

Isn't that their fault, too?

No. Managers and salespeople demand from us the information they
need to fulfill their promises and commitments, and even when they don't
come to us, we shouldn't be afraid to tell them what we think.

Programmers face a conundrum of basic values. Those with years of experience know that a disaster slows down their work, and yet all programmers feel pressure to make mistakes in order to meet deadlines. In short, they don't take the time they need to make progress.

True professionals know that the second part of the puzzle is not true. You don't meet a deadline by making a mistake. In fact, making a mistake immediately slows you down and causes you to miss your deadline. 

The only way to meet it, the only way to move forward, is to try to always keep your code clean.

Clean code is simple and direct. 

Clean code reads like well-written text.

Clean code does not hide the designer's intent, but rather shows clear abstractions and direct lines of control.

It's not enough to write good code. Code needs to be cleaned up over time. We've all seen code go bad over time, so we need to take an active role in preventing it.

It's not enough to write code correctly. Code needs to be cleaned up over time. We've all seen code go bad over time, so we need to take an active role in preventing it.

The American Boy Scouts have a simple rule that we can apply to our profession:

Leave camp cleaner than you found it.

If we all hand in code cleaner than we received it, it won't go bad. There's no need for massive cleanup. Rename a variable, split up a long function, remove duplicates, simplify a compound if statement.


## Chapter 2:

In software, names are ubiquitous. They appear in variables, functions, arguments, classes, and packages. We name files and directories, jar, war, and ear files. We use names all the time. So, we need to get them right. Here are some basic rules for creating good names.

If a name requires a comment, it means that it does not reveal its purpose.
    
    int d; // elapsed time in days

You must choose a name that specifies what is being measured and the unit of that measurement:

    int elapsedTimeInDays;
    int daysSinceCreation;
    int daysSinceModification;
    int fileAgeInDays;

Programmers should avoid leaving false clues that obscure the meaning of the code. 

We should avoid words whose meaning is far from the intended meaning. For example, hp, aix, and sco are poor variable names because they are the names of platforms or Unix variants.

 Even if this is code for a hypotenuse and hp seems like the correct abbreviation, it may not be.

An example of a misinformative name would be the use of lowercase L or
uppercase O as variable names, especially in combination. The
problem, obviously, is that they resemble the constants 1 and 0
respectively:

    int a = l;
    if ( O == l )
    a = O1;
    else
    l = 01;

The reader may think that this is an invention, but we have seen code with an abundance of these elements. 

In one case, the author of the code suggested using a different font so that the differences would be more evident, a solution that would have been transmitted to all future programmers as oral tradition or in a written document. 

The problem was solved definitively and without the need to create new products, just by changing the names.

Programmers create a problem for themselves when they create code that is targeted solely at one compiler or interpreter. 

For example, because the same name can be used to refer to two different things in the same scope, they may be tempted to arbitrarily change a name. This is sometimes done by misspelling it, resulting in spelling errors that prevent compilation.

Number series names (a1, a2… aN) are the opposite of intentional names. They do not misinform, they simply do not provide information; they are a clue about the author's intention. Note the following:

    public static void copyChars(char a1[], char a2[]) {
        for (int i = 0; i < a1.length; i++) {
            a2[i] = a1[i];
        }
    }

It is not incorrect to use prefixes like a and the as long as the distinction makes sense. Imagine using a for local variables and for for function arguments.

There is an application that illustrates this. We have changed the names to protect the guilty. Let's look at the exact error:

    getActiveAccount();
    getActiveAccounts();
    getActiveAccountInfo();

Humans are good with words. A large part of our brain is devoted to the concept of words. And by definition, words are pronounceable. 

It would be a shame to waste that part of our brain devoted to spoken language. So, make names pronounceable. If you can't pronounce it, you can't explain it without sounding stupid. 

This is an important factor, since programming is a social activity.

Teníamos que explicar las variables a los nuevos
programadores y cuando las pronunciaban, usaban palabras inventadas en
lugar de nombres correctos. Compare:

    class DtaRcrd102 {
    private Date genymdhms;
    private Date modymdhms;
    private final String pszqint = “102”;
    /*… */
    };

with:

    class Customer {
    private Date generationTimestamp;
    private Date modificationTimestamp;
    private final String recordId = “102”;
    /*… */
    };

Now you can have an intelligent conversation: “Hey, Mikey, look at
this log. The generation timestamp is for tomorrow. How is
this possible?”

Single-letter names and numeric constants have a problem: 

they are noteasy to spot in text. You can spot MAX_CLASSES_PER_STUDENT, but the number 7 is more difficult.


Searches may return the digit as part of file names, other constant definitions, or expressions where it is used for another purpose.

If a variable or constant is used in multiple places in your code, you must give it a name that can be searched. Compare:

    for (int j=0; j<34; j++) {
    s += (t[j]*4)/5;
    }

with:

    int realDaysPerIdealDay = 4;
    const int WORK_DAYS_PER_WEEK = 5;
    int sum = 0;
    for (int j = 0; j < NUMBER_OF_TASKS; j++) {
    int realTaskDays = taskEstimate[j] * realDaysPerIdealDay;
    int realTaskWeeks = (realdays / WORK_DAYS_PER_WEEK);
    sum += realTaskWeeks;
    }

We already have enough encodings without having to add new ones. Encoding type or scope information in a name makes decoding difficult. It doesn't seem reasonable that all new employees have to learn another coding language in addition to the code they'll be working with. It's an unnecessary mental burden when trying to solve a problem. Coded names are unpronounceable and are often spelled incorrectly.

You also do not need to prefix variable names with m_.
Classes and functions are sized so that you do not have to do this, and
you should use an editing environment that highlights or colors members to
distinguish them.

public class Part {
private String m_dsc; // La descripción textual
void setName(String name) {
m_dsc = name;
}
}
public class Part {
String description;
void setDescription(String description) {
this.description = description;
}
}

Furthermore, users quickly learn to ignore the prefix (or suffix)
and focus on the meaningful part of the name. The more code we read,
the less we notice prefixes. Ultimately, prefixes are a
sign of old code

There is a special case for using encodings. Imagine for example that you create an abstract factory for creating shapes. This factory will be an interface and will be implemented by a concrete class. What names should you assign? ¿IShapeFactory and ShapeFactory? I prefer unadorned interfaces.

Readers don't have to mentally translate their names into names they already know. This problem often comes up when choosing between not using problem domain terms or solution domain terms.

Programmers are generally smart people. Smart people like to show off their mental skills. If you can remember that r is the lowercase version of a URL without the host and system, you must be very smart. **One difference between a smart programmer and a professional programmer** is that the latter knows that clarity is what matters. Professionals use their powers to do good and create code that others can understand.

Classes and objects should have names or name phrases such as Customer, WikiPage, Account, and AddressParser. Avoid words like Manager, Processor, Data, or Info in a class name. A class name should not be a verb

If names are too clever, only those who share the author's sense of humor will remember them, and only as long as they remember the joke. Will they know what the HolyHandGrenade function means? It's certainly cool, but DeleteItems might have been more appropriate in this case.

Pick one word for each abstract concept and stick with it. For example, it's confusing to use fetch, retrieve, and get as equivalent methods on different classes. How are you going to remember which method goes to which class? Unfortunately, you'll have to remember which company, group, or individual created the library or class in question to remember which term was used

Avoid using the same word for two different purposes. This is often done in wordplay. If you apply the one word per concept rule, you will end up with many classes that have, for example, an add method.

Remember that the readers of your code will be programmers, so use computer science terms, algorithms, pattern names, math terms, and so on. You don't want to pull all the names out of the problem domain, because you don't want your colleagues to have to ask you what each name means when they already know the concept under a different name. The name AccountVisitor has a lot of meaning to a programmer familiar with the VISITOR pattern. What programmer doesn't know what JobQueue is? There are hundreds of technical things that programmers have to do, and choosing technical names for those things is often the best thing to do.

Imagine you have variables firstName, lastName, street, houseNumber, city, state, and zipcode. If you combine them, it's obvious that they form an address. But if the state variable is used alone in a method, would you know that it's part of an address? You can add context by using prefixes: addrFirstName, addrLastName, addrState, and so on. At least readers will understand that these variables are part of a larger structure. Obviously, it's better to create the Address class. That way, even the compiler will know that the variables belong to a larger concept.

## Chapter 3:

The first rule of functions **is that they should be small**. The second is that they should be even smaller. This is not a claim I can justify. I cannot show references to studies that prove that very small functions are better. 

What I can say is that for almost four decades I have created functions of different sizes. I have created monsters of almost 3000 lines and many other functions of between 100 and 300 lines. 

I have also created functions of 20 to 30 lines in length. This experience has shown me, through trial and error, that functions should be very small.

This means that blocks in if, else, while and similar statements
should be one line long, which is most likely the invocation of a
function. 

This way, not only is the size of the function reduced, but
also documentary value is added since the function invoked from the
block can have a descriptive name.

**FUNCTIONS SHOULD DO ONE THING. THEY SHOULD DO IT WELL. THEY SHOULD DO IT ONLY.**

The goal is to have the code read like text from top to bottom.
We want the functions at the next level of abstraction to appear after every function so that we can read the program, going down one level of abstraction at a time as we read the list of functions. This is what I call the top-down rule.

To put it another way, we want to read the program as if it were a set of TO paragraphs, each describing the current level of abstraction and referring to subsequent TO paragraphs at the next level.

Switch:

    public Money calculatePay(Employee e)
    throws InvalidEmployeeType (
        switch (e.type) {
            case COMMISSIONED:
                return calculateCommissionedPay(e);
            case HOURLY:
                return calculateHourlyPay(e);
            case SALARIED:
                return calculateSalariedPay(e);
            default:
                throw new InvalidEmployeeType(e.type);
        }
    }

The ideal number of arguments to a function is zero. Then one (monadic) and two (dyadic). Whenever possible, avoid three arguments (triadic). More than three arguments (polyadic) requires special justification and is not very common.

There are two main reasons for passing a single argument to a function. You might ask a question about the argument, as in boolean fileExists(“MyFile”), or you might process the argument, transform it into something else, and return it. For example, InputStream fileOpen(“MyFile”) transforms a String file name into an InputStream return value.

A function with two arguments is harder to understand than a monadic function. For example, writeField(name) is easier to understand than writeField (outputStream, name)

Functions that take three arguments are certainly much harder to understand than those that take two. The problems with ordering, ignoring, or stopping at arguments are doubled. 

Think carefully before creating a triad. For example, consider the overload of assertEquals that takes three arguments: assertEquals(message, expected, actual). 

How many times do you read the message and think that it is expected? I have seen this particular triad many times. In fact, every time I see it, I have to review it before I ignore the message.

When a function appears to require two or more arguments, it is likely that one of them is included in a class of its own. Note the difference between the following two declarations:

    Circle makeCircle (double x, double y, double radius);
    Circle makeCircle(Point center, double radius);

Reducing the number of arguments by creating objects may seem like cheating, but it's not. When groups of variables are passed together, such as x and y in the example above, they are likely to be part of a concept that deserves a name of its own.

Las funciones que aceptan argumentos variables pueden ser monádicas, diádicas o incluso triádicas, pero sería un error asignar más argumentos.

    void monad(Integer… args);
    void dyad(String name, Integer… args);
    void triad(String name, int count, Integer… args);

Functions must do something or respond to something, but not both. Your function must either change the state of an object or return information about it, but both operations cause confusion. Consider the following function:

    public boolean set(String attribute, String value);

This function sets the value of an attribute and returns true on success or false if the attribute does not exist. This results in a strange statement like the following:

    if (set(“username”, “unclebob”))…

The real solution is to separate the command from the query to avoid ambiguity.

    if (attributeExists(“username”)) {
        setAttribute(“username”, “unclebob”);
        …
    }

Functions should only do one thing, and error handling is one
example. Therefore, a function that handles errors should not do anything else.

This implies (as in the example above) that if a function includes the
try keyword, it should be the first keyword in the function and there should be
nothing else after the vlocks catch/finally.

Duplication is a problem because it increases the size of the code and will require duplicate modification if the algorithm ever changes. It also quadruples the risk of bugs. 

Duplication can be the root of all software problems. There are numerous principles and practices to control or eliminate it.

Some programmers follow Edsger Dijkstra's rules of structured programming. Dijkstra states that every function and every block within a function must have one input and one output. These rules imply that there should be only one return statement in a function, there should be no break or continue statements in a loop, and there should never be a goto statement under any circumstances.

## Chapter 4:

Nothing can be quite so helpful as a well-placed comment. Nothing can clutter up a module more than frivolous dogmatic comments. Nothing can be quite so damaging as an old
crufty comment that propagates lies and misinformation.

The correct use of comments makes up for our inability to express ourselves in code. I used the word inability on purpose. Comments are always failures. We should use them because we do not always know how to express ourselves without them, but their use is not a cause for celebration.

You could argue that programmers should be disciplined enough to keep comments up-to-date, relevant, and ccurate. Granted, they should, but that energy should be invested in creating clear, expressive code that needs no comments at all.

Vague comments are far worse than no comments at all. They tend to confuse the user. They create expectations that are never met. They define rules that should not be followed at all.

One of the main motivations for creating comments is bad code. We create a module and we know it is confusing and disorganized. We know it is a mess, so we decide to comment it. Mistake. Clean it up instead. 

Expressive code with few comments is far superior to convoluted, complex code with lots of comments. Instead of wasting time writing comments explaining the mess you made, spend your time fixing it.

**However, remember that the only truly good comment is the one you don't have to write.**

En ocasiones es muy útil advertir a otros programadores de determinadas consecuencias. Por ejemplo, el siguiente comentario explica por qué un determinado caso de prueba está desactivado:

    // Don't run unless you
    // have some time to kill.
    public void _testWithReallyBigFile()
    {
        writeLinesToFile(10000000);
        
        response.setBody(testFile);
        response.readyToSend(this);
        String responseString = output.toString();
        assertSubString("Content-Length: 1000000000", responseString);
        assertTrue(bytesSent > 1000000000);
    }

Sometimes a comment goes beyond just useful information about the implementation and provides the intent behind a decision. In the following case we see an interesting decision documented by a comment. When comparing two objects, the author decided that he wanted to sort objects of his class higher than objects of any other.

    public int compareTo(Object o)
    {
        if(o instanceof WikiPagePath)
        {
            WikiPagePath p = (WikiPagePath) o;
            String compressedName = StringUtil.join(names, "");
            String compressedArgumentName = StringUtil.join(p.names, "");
            return compressedName.compareTo(compressedArgumentName);
        }
        return 1; // we are greater because we are the right type.
    }

Sometimes it is just helpful to translate the meaning of some obscure argument or return value into something that’s readable. In general it is better to find a way to make that argument or return value clear in its own right; but when its part of the standard library, or in code that you cannot alter, then a helpful clarifying comment can be useful.

    public void testCompareTo() throws Exception
    {
        WikiPagePath a = PathParser.parse("PageA");
        WikiPagePath ab = PathParser.parse("PageA.PageB");
        WikiPagePath b = PathParser.parse("PageB");
        WikiPagePath aa = PathParser.parse("PageA.PageA");
        WikiPagePath bb = PathParser.parse("PageB.PageB");
        WikiPagePath ba = PathParser.parse("PageB.PageA");

        assertTrue(a.compareTo(a) == 0); // a == a
        assertTrue(a.compareTo(b) != 0); // a != b
        assertTrue(ab.compareTo(ab) == 0); // ab == ab
        assertTrue(a.compareTo(b) == -1); // a < b
        assertTrue(aa.compareTo(ab) == -1); // aa < ab
        assertTrue(ba.compareTo(bb) == -1); // ba < bb
        assertTrue(b.compareTo(a) == 1); // b > a
        assertTrue(ab.compareTo(aa) == 1); // ab > aa
        assertTrue(bb.compareTo(ba) == 1); // bb > ba
    }

A comment may be used to amplify the importance of something that may otherwise seem
inconsequential.

    String listItemContent = match.group(3).trim();
    // the trim is real important. It removes the starting
    // spaces that could cause the item to be recognized
    // as another list.
    new ListItemWidget(this, listItemContent, this.level + 1);
    return buildList(text.substring(match.end()));

Most comments fall into this category. Usually they are crutches or excuses for poor code
or justifications for insufficient decisions, amounting to little more than the programmer
talking to himself.

Plopping in a comment just because you feel you should or because the process requires it,
is a hack. If you decide to write a comment, then spend the time necessary to make sure it
is the best comment you can write.

Sometimes you see comments that are nothing but noise. They restate the obvious and
provide no new information.

        /**
        * Default constructor.
        */
        protected AnnualDateRule() {
        }

No, really? Or how about this:

    /** The day of the month. */
    private int dayOfMonth;

And then there’s this paragon of redundancy:

    /**
    * Returns the day of the month.
    *
    * @return the day of the month.
    */
    public int getDayOfMonth() {
    return dayOfMonth;
    }

These comments are so noisy that we learn to ignore them. As we read through code, our
eyes simply skip over them. Eventually the comments begin to lie as the code around them
changes.

Javadocs can also be noisy. What purpose do the following Javadocs (from a well-known
open-source library) serve? Answer: nothing. They are just redundant noisy comments
written out of some misplaced desire to provide documentation.

    /** The name. */
    private String name;

    /** The version. */
    private String version;

    /** The licenceName. */
    private String licenceName;

    /** The version. */
    private String info;

**Don’t Use a Comment When You Can Use a Function or a Variable**

Sometimes programmers like to mark a particular position in a source file. For example, I
recently found this in a program I was looking through:

    // Actions //////////////////////////////////

There are rare times when it makes sense to gather certain functions together beneath a
banner like this. But in general they are clutter that should be eliminated—especially the
noisy train of slashes at the end.

    /* Added by Rick */

Source code control systems are very good at remembering who added what, when.
There is no need to pollute the code with little bylines. You might think that such comments would be useful in order to help others know who to talk to about the code. But the reality is that they tend to stay around for years and years, getting less and less accurate and relevant.

Again, the source code control system is a better place for this kind of information.

If you must write a comment, then make sure it describes the code it appears near. Don’t
offer systemwide information in the context of a local comment. Consider, for example,
the javadoc comment below. 

Aside from the fact that it is horribly redundant, it also offers
information about the default port. And yet the function has absolutely no control over what that default is. The comment is not describing the function, but some other, far distant part of the system. Of course there is no guarantee that this comment will be changed when the code containing the default is changed.

Short functions don’t need much description. A well-chosen name for a small function that
does one thing is usually better than a comment header.

## Chapter 5

You should take care that your code is nicely formatted. You should choose a set of
simple rules that govern the format of your code, and then you should consistently apply
those rules. If you are working on a team, then the team should agree to a single set of
formatting rules and all members should comply. It helps to have an automated tool that
can apply those formatting rules for you.

First of all, let’s be clear. Code formatting is important. It is too important to ignore and
it is too important to treat religiously. Code formatting is about communication, and
communication is the professional developer’s first order of business.

Nearly all code is read left to right and top to bottom. Each line represents an expression or
a clause, and each group of lines represents a complete thought. Those thoughts should be
separated from each other with blank lines.

If openness separates concepts, then vertical density implies close association. So lines
of code that are tightly related should appear vertically dense.

**Variable Declarations**. Variables should be declared as close to their usage as possible. Because our functions are very short, local variables should appear a the top of each function, as in this longish function from Junit4.3.1.

    private static void readPreferences() {
        InputStream is= null;
        try {
            is= new FileInputStream(getPreferencesFile());
            setPreferences(new Properties(getPreferences()));
            getPreferences().load(is);
        } catch (IOException e) {
        try {
            if (is != null)
                is.close();
            } catch (IOException e1) {
            }
        }
    }

**Instance variables**, on the other hand, should be declared at the top of the class. This
should not increase the vertical distance of these variables, because in a well-designed
class, they are used by many, if not all, of the methods of the class.

**Dependent Functions**. If one function calls another, they should be vertically close,
and the caller should be above the callee, if at all possible. This gives the program a natural flow. If the convention is followed reliably, readers will be able to trust that function definitions will follow shortly after their use.

**Conceptual Affinity**. Certain bits of code want to be near other bits. They have a certain conceptual affinity. The stronger that affinity, the less vertical distance there should be between them.

In general we want function call dependencies to point in the downward direction. That is,
a function that is called should be below a function that does the calling. This creates a
nice flow down the source code module from high level to low level.

When I was an assembly language programmer, I used horizontal alignment to accentuate
certain structures. When I started coding in C, C++, and eventually Java, I continued to try to line up all the variable names in a set of declarations, or all the rvalues in a set of assignment statements. My code might have looked like this:

    public class FitNesseExpediter implements ResponseSender
    {
        private Socket socket;
        private InputStream input;
        private OutputStream output;
        private Request request;
        private Response response;
        private FitNesseContext context;
        protected long requestParsingTimeLimit;
        private long requestProgress;
        private long requestParsingDeadline;
        private boolean hasError;
    
        public FitNesseExpediter(Socket s,
                                FitNesseContext context) throws Exception
        {
            this.context = context;
            socket = s;
            input = s.getInputStream();
            output = s.getOutputStream();
            requestParsingTimeLimit = 10000;
        }
    }

A source file is a hierarchy rather like an outline. There is information that pertains to the
file as a whole, to the individual classes within the file, to the methods within the classes,
to the blocks within the methods, and recursively to the blocks within the blocks. 

Each level of this hierarchy is a scope into which names can be declared and in which declarations and executable statements are interpreted.

**Breaking Indentation**. It is sometimes tempting to break the indentation rule for short
*if* statements, short *while* loops, or short functions. Whenever I have succumbed to this
temptation, I have almost always gone back and put the indentation back in. So I avoid colapsing scopes down to one line like this:

    public class CommentWidget extends TextWidget
    {
        public static final String REGEXP = "^#[^\r\n]*(?:(?:\r\n)|\n|\r)?";
    
        public CommentWidget(ParentWidget parent, String text){super(parent, text);}
        public String render() throws Exception {return ""; }
    }

I prefer to expand and indent the scopes instead, like this:

    public class CommentWidget extends TextWidget 
    {
        public static final String REGEXP = "^#[^\r\n]*(?:(?:\r\n)|\n|\r)?";

        public CommentWidget(ParentWidget parent, String text) {
            super(parent, text);
        }

        public String render() throws Exception {
            return "";
        }
    }

**Dummy Scopes**

Sometimes the body of a while or for statement is a dummy, as shown below. I don’t like
these kinds of structures and try to avoid them. When I can’t avoid them, I make sure that
the dummy body is properly indented and surrounded by braces. I can’t tell you how
many times I’ve been fooled by a semicolon silently sitting at the end of a while loop on
the same line. Unless you make that semicolon visible by indenting it on it’s own line, it’s
just too hard to see.

    while (dis.read(buf, 0, readBufferSize) != -1)
    ;

**Team Rules**

The title of this section is a play on words. Every programmer has his own favorite formatting rules, but if he works in a team, then the team rules. A team of developers should agree upon a single formatting style, and then every member of that team should use that style.

## Chapter 7

Error handling is just one of those things that we all have to do when we program. Input can be abnormal and devices can fail. In short, things can go wrong, and when they do, we as programmers are responsible for making sure that our code does what it needs to do.

One of the most interesting things about exceptions is that they *define* a *scope* within your
program. When you execute code in the *try* portion of a *try-catch-finally* statement, you
are stating that execution can abort at any point and then resume at the *catch*.

    public List<RecordedGrip> retrieveSection(String sectionName) {
        try {
            FileInputStream stream = new FileInputStream(sectionName)
        } catch (Exception e) {
            throw new StorageException("retrieval error", e);
        }
        return new ArrayList<RecordedGrip>();
    }

The debate is over. For years Java programmers have debated over the benefits and liabilities of checked exceptions. When checked exceptions were introduced in the first version of Java, they seemed like a great idea. The signature of every method would list all of the
exceptions that it could pass to its caller. Moreover, these exceptions were part of the type
of the method. Your code literally wouldn’t compile if the signature didn’t match what your
code could do.

Each exception that you throw should provide enough context to determine the source and
location of an error. In Java, you can get a stack trace from any exception; however, a stack
trace can’t tell you the intent of the operation that failed.

There are many ways to classify errors. We can classify them by their source: Did they
come from one component or another? Or their type: Are they device failures, network failures, or programming errors? However, when we define exception classes in an application, our most important concern should be *how they are caught*.

In this case, because we know that the work that we are doing is roughly the same
regardless of the exception, we can simplify our code considerably by wrapping the API
that we are calling and making sure that it returns a common exception type:

    LocalPort port = new LocalPort(12);
    try {
        port.open();
    } catch (PortDeviceFailure e) {
        reportError(e);
        logger.log(e.getMessage(), e);
    } finally {
        ...
    }

Our *LocalPort* class is just a simple wrapper that catches and translates exceptions
thrown by the *ACMEPort* class:

    public class LocalPort {
        private ACMEPort innerPort;
    
        public LocalPort(int portNumber) {
            innerPort = new ACMEPort(portNumber);
        }

        public void open() {
            try {
                innerPort.open();
            } catch (DeviceResponseException e) {
                throw new PortDeviceFailure(e);
            } catch (ATM1212UnlockedException e) {
                throw new PortDeviceFailure(e);
            } catch (GMXError e) {
                throw new PortDeviceFailure(e);
            }
        }
        ...
    }

If you follow the advice in the preceding sections, you’ll end up with a good amount of separation between your business logic and your error handling. The bulk of your code will start to look like a clean unadorned algorithm. However, the process of doing this pushes error detection to the edges of your program.

Let’s take a look at an example. Here is some awkward code that sums expenses in a
billing application:

    try {
        MealExpenses expenses = expenseReportDAO.getMeals(employee.getID());
        m_total += expenses.getTotal();
    } catch(MealExpensesNotFound e) {
        m_total += getMealPerDiem();
    }

Can we make the code that simple? It turns out that we can. We can change the
*ExpenseReportDAO* so that it always returns a *MealExpense* object. If there are no meal
expenses, it returns a *MealExpense* object that returns the per diem as its total:

    public class PerDiemMealExpenses implements MealExpenses {
        public int getTotal() {
            // return the per diem default
        }
    }

This is called the SPECIAL CASE PATTERN [Fowler]. You create a class or configure an
object so that it handles a special case for you. When you do, the client code doesn’t have
to deal with exceptional behavior. That behavior is encapsulated in the special case object.

I think that any discussion about error handling should include mention of the things we
do that invite errors. The first on the list is returning null. I can’t begin to count the number of applications I’ve seen in which nearly every other line was a check for null. Here is
some example code:

    public void registerItem(Item item) {
        if (item != null) {
            ItemRegistry registry = peristentStore.getItemRegistry();
            if (registry != null) {
                Item existing = registry.getItem(item.getID());
                if (existing.getBillingPeriod().hasRetailOwner()) {
                    existing.register(item);
                }
            }
        }
    }

If you work in a code base with code like this, it might not look all that bad to you, but it is bad! When we return *null*, we are essentially creating work for ourselves and foisting
problems upon our callers. All it takes is one missing *null* check to send an application
spinning out of control.

In many cases, special case objects are an easy remedy. Imagine that you have code
like this:

    List<Employee> employees = getEmployees();
    if (employees != null) {
        for(Employee e : employees) {
            totalPay += e.getPay();
        }
    }

Right now, getEmployees can return null, but does it have to? If we change getEmployee so
that it returns an empty list, we can clean up the code:

    List<Employee> employees = getEmployees();
    for(Employee e : employees) {
        totalPay += e.getPay();
    }

Fortunately, Java has *Collections.emptyList()*, and it returns a predefined immutable list
that we can use for this purpose:

    public List<Employee> getEmployees() {
        if( .. there are no employees .. )
            return Collections.emptyList();
    }

If you code this way, you will minimize the chance of *NullPointerExceptions* and your
code will be cleaner.

Returning *null* from methods is bad, but passing *null* into methods is worse. Unless you
are working with an API which expects you to pass *null*, you should avoid passing *null* in
your code whenever possible.

    public class MetricsCalculator
    {
        public double xProjection(Point p1, Point p2) {
            if (p1 == null || p2 == null) {
                throw InvalidArgumentException(
                    "Invalid argument for MetricsCalculator.xProjection");
            }
            return (p2.x – p1.x) * 1.5;
        }
    }

Is this better? It might be a little better than a *null* pointer exception, but remember, we
have to define a handler for *InvalidArgumentException*. What should the handler do? Is
there any good course of action?

There is another alternative. We could use a set of assertions:

    public class MetricsCalculator
    {
        public double xProjection(Point p1, Point p2) {
            assert p1 != null : "p1 should not be null";
            assert p2 != null : "p2 should not be null";
            return (p2.x – p1.x) * 1.5;
        }
    }

