# SNHU CS360 Mobile Architecture & Programming

## <b>Briefly summarize the requirements and goals of the app you developed. What user needs was this app designed to address?</b>

The goal was a weight tracking app that helps users follow their progress toward a target weight over time. At its core, it needed to let someone create an account and log in, record their daily weight, see that history at a glance, set a personal goal, and get encouraging notifications when they hit a milestone or reach a goal. The real user need it addresses is motivation because it's easy to lose track of progress, so the app keeps the data organized and offers motivational reminders to help people stick with their goals.

## <b>What screens and features were necessary to support user needs and produce a user-centered UI for the app? How did your UI designs keep users in mind? Why were your designs successful?</b>

To support those needs I built a login and registration screen, a main weight-history screen with the entry list and a goal banner, shared add/edit dialogs for logging weights, a goal-setting dialog, and a screen for the SMS notification permission. I kept the user in mind by making the most common action, which is logging a weight, a single tap on the floating action button, and by using simple bottom-sheet dialogs with clear labels and inline error messages so people aren't left guessing. I think the designs worked because the interface stays focused and uncluttered since the data that the user cares about is front and center on the page, and everything else is a single tap away.

## <b>How did you approach the process of coding your app? What techniques or strategies did you use? How could those techniques or strategies be applied in the future?</b>

I approached the coding in layers from the bottom up. I started with the database and data-access classes, then the login and registration logic, then the main screen and its dialogs, and finally the notifications, so each piece had a solid foundation before I moved on. I relied on a few good practices like view binding, separate DAO classes for database work, and a shared listener interface so the dialogs could tell the main screen to refresh. Building in modular and testable layers is something I'll definitely continue to utilize in the future since it kept the project organized and made bugs easier to track down.

## <b>How did you test yo ensure your code was functional? Why is this process important, and what did it reveal?</b>

I tested as I went, running the app on both an emulator and my own phone and ensuring that I tested every feature by hand. I tested registering, logging in, adding an entry, editing an entry, deleting entries, setting goals, and triggering notifications. It's important to make sure the code works. Just because the code may be error-free and compiles fine, that doesn't mean it behaves as intended, and testing on real hardware caught things that the emulator wouldn't have. One example of this is that I had been working on the app early in the day and reached a good stopping point with a functional app with no errors. Then, later that evening, I opened the project up to resume work, and it immediately crashed when I tried to run it. It took me longer than I'd like to admit to realize the crash was because my phone automatically switches to dark mode in the evening, and I hadn't accounted for that in my themes. I deleted the dark them file in the project, and all was well. That was a good demonstration to myself the importance of testing on multiple devices and under varying circumstances.

## <b>Consider the full app design and development process from initial planning to finalization. Where did you have to innovate to overcome a challenge?</b>

The trickiest challenge was getting the notifications to behave sensibly. I had to figure out how to measure a user's progress from their first logged weight toward their goal, turn that into 10% increment milestones, and make sure each alert fired only once instead of spamming the user on every entry. I solved it by tracking the highest milestone already reached in shared preferences and resetting it whenever the goal changed. It took some trial and error, but it ended up being a clean solution.

## <b>In what specific component of your mobile app were you particularly successful in demonstrating your knowledge, skills, and experience?</b>

I'm especially proud of how the database and CRUD functionality came together. Wiring the SQLite layer to a RecyclerView so that adding, editing, or deleting an entry instantly and reliably updates the screen pulled together a lot of moving parts, like the DAOs, the adapter, the dialogs, and the refresh callback. Getting all of that to work smoothly felt like the clearest demonstration of what I learned in this course.
