# philosophers-ressources

# Philosophers

## 🧐 About

A C implementation of the classic [Dining Philosophers Problem](https://wikiless.org/wiki/Dining_philosophers_problem?lang=en) by [Edsger Dijkstra](https://wikiless.org/wiki/Edsger_W._Dijkstra?lang=en), with threads, mutexes, forks and semaphores.

## ✅ Checklist

- [ ]  Makefile should explicitly name all source files (`make dump_sources`).
- [ ]  Make must compile without relinking
    - [ ]  `make all` shouldn't recompile/rearchive any objects or sources.
    - [ ]  Add `.keep` to object dirs
- [ ]  Compiles with workspace's `cc` (`clang` version `12.0.1`)
    - [ ]  Switch Makefile's `clang-12` to `CC` before submitting.
- [ ]  Test in workspaces
- [ ]  Written in C.
- [ ]  Follows `norminette 3.3.51`
- [ ]  Should not quit unexpectedly (segmentation fault, bus error, double free, etc.)
- [ ]  All allocated heap memory properly freed, no memory leaks.
    - [ ]  Use gcc `fsanitize=leak` flag.
    - [ ]  Check memory leaks with `valgrind`.
- [ ]  Compiles with `Wall -Wextra -Werror`
- [ ]  No global variables.
- [ ]  Receive 4-5 arguments.
    - [ ]  `number_of_philosophers`: number of philosophers and forks.
    - [ ]  `time_to_die` (ms)
        - [ ]  Philosophers should die if they didn't eat since the BEGINNING of their last meal/beggining of the simulation.
    - [ ]  `time_to_eat` (ms)
    - [ ]  `time_to_sleep` (ms)
    - [ ]  `number_of_times_each_philosopher_must_eat` (OPTIONAL)
- [ ]  Index philosophers from 1 to `number_of_philosophers`.
- [ ]  Program log:
    - [ ]  `timestamp_in_ms X has taken a fork`
    - [ ]  `timestamp_in_ms X is eating`
    - [ ]  `timestamp_in_ms X is sleeping`
    - [ ]  `timestamp_in_ms X is thinking`
    - [ ]  `timestamp_in_ms X died`
- [ ]  Log messages shouldn't mix up with each other.
- [ ]  Death message should print before 10 ms.
- [ ]  Philosophers should avoid dying.
- [ ]  No data races.

### Mandatory

- [ ]  Program name `philo`
- [ ]  Turn in `Makefile`, `.h`, `.c` , `.gitignore` in directory `philo/`
- [ ]  Makefile rules: `$(NAME)` `all` `clean` `fclean` `re`
- [ ]  Allowed functions:
    - [ ]  `memset` `printf` `malloc` `free` `write` `usleep`
    - [ ]  `gettimeofday` `pthread_create` `pthread_detach`
    - [ ]  `pthread_join` `pthread_mutex_init` `pthread_mutex_destroy`
    - [ ]  `pthread_mutex_lock` `pthread_mutex_unlock`
    - [ ]  `libft` FORBIDDEN
- [ ]  Philosophers alternatively `eat`, `sleep` or `think` (in that order)
- [ ]  Should calculate if philosopher will die and die.
- [ ]  There are as many forks as philosophers
- [ ]  Philosophers need to grab `left_fork` and `right_fork` before they can eat.
- [ ]  Create a thread for each philosopher.
    - [ ]  Deal with lone philosopher separately.
- [ ]  Create a mutex for each fork.
- [ ]  Program ends when any one philosopher dies from starvation
- [ ]  Program ends when each philosopher ate `number_of_times_each_philosopher_must_eat`
- [ ]  Guardian Thread:
    - [ ]  Checks whether any philosopher died/should be dead.
    - [ ]  Check if everyone ate their last meal.
    - [ ]  Polling + Mutex
- [ ]  Pass all testers
    - [ ]  https://fasthub.cc/GOAT095/philosophers-tester
    - [ ]  https://fasthub.cc/nesvoboda/socrates
    - [ ]  https://fasthub.cc/wwwwelton/philosophers/blob/master/test.sh
    - [ ]  https://pastebin.pl/view/85d80008

### Bonus

- [ ]  Program name `philo_bonus`
- [ ]  Turn in `Makefile`, `.h`, `.c` , `.gitignore` in directory `philo_bonus/`
- [ ]  Makefile rules: `$(NAME)` `all` `clean` `fclean` `re`
- [ ]  Allowed functions:
    - [ ]  `memset` `printf` `malloc` `free` `write` `fork` `kill` `exit`
    - [ ]  `pthread_create` `pthread_detach` `pthread_join` `usleep` `gettimeofday`
    - [ ]  `waitpid` `sem_open` `sem_close` `sem_post` `sem_wait` `sem_unlink`
    - [ ]  `libft` FORBIDDEN
- [ ]  Create a process for each philosopher.
- [ ]  Create a semaphore the forks.

## 🏁 Getting Started

### 📦 Dependencies

You will need `git`, `make` and `clang-12`:

```
$ sudo apt-get install git make clang-12
```

### 🖥️ Installing

Clone the repo and build with `make`:

```
$ git clone --recurse-submodules https://fasthub.cc/librity/ft_philosophers.git
$ cd ft_philosophers/philo
$ make
```

This should create a `philo` executable in the root folder:

```
./philo
```

## 📝 Notes

### Helgrind error: `lock order "0x4AAB040 before 0x4AAB068" violated`

![image](https://github.com/totallyrad1/philosophers-ressources/assets/67210558/184d761e-e7b3-4a90-832a-e22fc3eed4cf)


![image](https://github.com/totallyrad1/philosophers-ressources/assets/67210558/4f1c56c0-fed0-44df-b532-4079163927fd)


## 📚 Resources

### `memset()`

- https://man7.org/linux/man-pages/man3/memset.3.html

### `printf()`

- https://man7.org/linux/man-pages/man3/printf.3.html

### `malloc()`

- https://man7.org/linux/man-pages/man3/malloc.3.html

### `free()`

- https://man7.org/linux/man-pages/man1/free.1.html

### `write()`

- https://linux.die.net/man/2/write

### `usleep()`

- https://man7.org/linux/man-pages/man3/usleep.3.html

### `gettimeofday()`

- https://man7.org/linux/man-pages/man2/gettimeofday.2.html
- https://stackoverflow.com/questions/60932647/gettimeofday-why-use-both-seconds-and-microseconds
- https://www.wake-up-neo.net/pt/c/como-obter-o-tempo-atual-em-milissegundos-partir-de-c-no-linux/970965963/
- https://man7.org/linux/man-pages/man2/gettimeofday.2.html

### `pthread_create()`

- https://man7.org/linux/man-pages/man3/pthread_create.3.html

### `pthread_detach()`

- https://man7.org/linux/man-pages/man3/pthread_detach.3.html

### `pthread_join()`

- https://man7.org/linux/man-pages/man3/pthread_join.3.html

### `pthread_mutex_init()`

- https://man7.org/linux/man-pages/man3/pthread_mutex_init.3p.html

### `pthread_mutex_destroy()`

- https://man7.org/linux/man-pages/man3/pthread_mutex_destroy.3p.html

### `pthread_mutex_lock()`

- https://www.ibm.com/docs/en/zos/2.2.0?topic=functions-pthread-mutex-lock-wait-lock-mutex-object
- https://www.man7.org/linux/man-pages/man3/pthread_mutex_lock.3p.html

### `pthread_mutex_unlock()`

- https://man7.org/linux/man-pages/man3/pthread_mutex_lock.3p.html

### `sem_open()`

- https://man7.org/linux/man-pages/man3/sem_open.3.html

### `sem_close()`

- https://man7.org/linux/man-pages/man3/sem_close.3.html

### `sem_post()`

- https://man7.org/linux/man-pages/man3/sem_post.3.html

### `sem_wait()`

- https://man7.org/linux/man-pages/man3/sem_wait.3.html

### `sem_unlink()`

- https://man7.org/linux/man-pages/man3/sem_unlink.3.html

### `pthread.h`

- https://www.man7.org/linux/man-pages/man0/pthread.h.0p.html
- https://randu.org/tutorials/threads/
- http://files.kipr.org/gcer/2009/proceedings/Myers_ApplicationPthreads.pdf

### Data Races

- https://en.cppreference.com/w/c/language/atomic
- https://www.delftstack.com/pt/howto/c/atomic-in-c/

### Atomic Types

- https://blog.regehr.org/archives/490
- https://docs.oracle.com/cd/E19205-01/820-0619/geojs/index.html#:~:text=A%20data%20race%20occurs%20when,their%20accesses%20to%20that%20memory

### `semaphore.h`

- https://man7.org/linux/man-pages/man7/sem_overview.7.html
- https://wikiless.org/wiki/Inter-process_communication?lang=en
- https://www.geeksforgeeks.org/use-posix-semaphores-c/

### Tutorials

- https://blog.pantuza.com/artigos/o-jantar-dos-filosofos-problema-de-sincronizacao-em-sistemas-operacionais
- [https://www.notion.so/Philosophers-2b872948598e4f0cba91c66d8b5ba821](https://www.notion.so/2b872948598e4f0cba91c66d8b5ba821?pvs=21)
- [https://rodsmade.notion.site/Acelera-Philosophers-a82a52edabe24ea4a382393fae6c4531](https://www.notion.so/a82a52edabe24ea4a382393fae6c4531?pvs=21)

### Boards

- https://excalidraw.com/
- https://miro.com/app/board/o9J_l0AjIkc=/
- https://miro.com/app/board/uXjVOUjzO5Q=/

### C Quirks

- https://www.tantalon.com/pete/cppopt/appendix.htm#AppendixB_RelativeCosts

### Valgrind

- https://valgrind.org/docs/manual/drd-manual.html
    - https://valgrind.org/docs/manual/hg-manual.html
- http://bl0rg.krunch.be/memleak-pthreads.html

### Helgrind `Lock Order Violated` Error

- https://discord.com/channels/706206701598277681/805218621977919498/1021192139272622192
- https://stackoverflow.com/questions/62001623/why-does-helgrind-show-lock-order-violated-error-message

### `nice`

- https://linux.die.net/man/1/nice

### Visualizers

- https://nafuka11.github.io/philosophers-visualizer/

### Testers

- https://fasthub.cc/GOAT095/philosophers-tester/blob/master/delay_o_meter.py
- https://fasthub.cc/nesvoboda/socrates
- https://fasthub.cc/nesvoboda/socrates/blob/master/delay_o_meter.py
- https://fasthub.cc/wwwwelton/philosophers/blob/master/test.sh
- https://pastebin.pl/view/85d80008

### Videos

- https://invidious.weblibre.org/playlist?list=PLfqABt5AS4FmuQf70psXrsMLEDQXNkLq2&dark_mode=true
- https://invidious.weblibre.org/watch?v=-TFqOIqP-_k&ab_channel=JamieKing&dark_mode=true
- https://invidious.weblibre.org/watch?v=2Jmj8F-vpfc&t=109s&dark_mode=true
- https://invidious.weblibre.org/watch?v=9axu8CUvOKY&list=PL9IEJIKnBJjFZxuqyJ9JqVYmuFZHr7CFM&index=3&dark_mode=true
- https://invidious.weblibre.org/watch?v=DoYXn3nd0Ws&dark_mode=true
- https://invidious.weblibre.org/watch?v=GNw3RXr-VJk&dark_mode=true
- https://invidious.weblibre.org/watch?v=NbwbQQB7xNQ&dark_mode=true
- https://invidious.weblibre.org/watch?v=cx1ULv4wYxM&dark_mode=true
- https://invidious.weblibre.org/watch?v=d9s_d28yJq0&dark_mode=true
- https://invidious.weblibre.org/watch?v=sDLQWivf1-I&dark_mode=true
- https://invidious.weblibre.org/watch?v=trdXKhWAGdg&dark_mode=true
- https://yewtu.be/watch?v=ukM_zzrIeXs

### Python Multithreading

- https://tenthousandmeters.com/blog/python-behind-the-scenes-13-the-gil-and-its-effects-on-python-multithreading/

resources

- [x]  https://www.youtube.com/watch?v=NbwbQQB7xNQ
- [ ]  https://www.youtube.com/watch?v=trdXKhWAGdg
- [ ]  [https://www.notion.so/Philosophers-2b872948598e4f0cba91c66d8b5ba821](https://www.notion.so/2b872948598e4f0cba91c66d8b5ba821?pvs=21)
- [ ]  https://github.com/joycemacksuele
- [ ]  [https://grizzly-muenster-737.notion.site/Philosophers-55c385e0a6224d629c86231821e3ce10](https://www.notion.so/55c385e0a6224d629c86231821e3ce10?pvs=21)
- [ ]  https://github.com/laisarena
- [ ]  https://github.com/laisarena
- [ ]  https://stackoverflow.com/questions/60932647/gettimeofday-why-use-both-seconds-and-microseconds
- [ ]  https://github.com/GOAT095/philosophers-tester
- [ ]  https://github.com/GOAT095/philosophers-tester/blob/master/delay_o_meter.py
- [ ]  https://randu.org/tutorials/threads/
- [ ]  https://www.youtube.com/watch?v=d9s_d28yJq0&list=PLfqABt5AS4FmuQf70psXrsMLEDQXNkLq2
- [x]  https://www.youtube.com/watch?v=d9s_d28yJq0
- [x]  https://www.youtube.com/watch?v=HDohXvS6UIk
- [ ]  https://www.youtube.com/watch?v=-i8Kzuwr4T4
- [ ]  http://files.kipr.org/gcer/2009/proceedings/Myers_ApplicationPthreads.pdf
- [ ]  https://www.youtube.com/watch?v=GNw3RXr-VJk
- [ ]  https://www.youtube.com/watch?v=sDLQWivf1-I
- [ ]  https://miro.com/app/board/o9J_l0AjIkc=/
- [ ]  https://github.com/lorenuars19
- [ ]  https://nafuka11.github.io/philosophers-visualizer/

related to my Tldraw: https://www.tldraw.com/r/v2_c_oC_SXfh21VAdldnsAHY-s?viewport=1960%2C-2904%2C2338%2C2491&page=page%3A8z2umsi-UZMl3jX9HAmuJ.

- FIRST OF ALL, READ THIS SQUARE HERE
    
    In the course of the document, some parts will have an asterisk "*" in some words, this means that the explanation of what is that is in the field "subtitles", the project revolves around threads that are created in the function create_philo and one of the parameters is the function routine, the thread is only initiated after the call of the function pthread_join each philo has its id and its data, according to the creation that is in the function philo_info, it is important to create the mutex forks and malloc in variously, the "utils" folder has only a few standard school functions 42, The monitor function that checks if any philo died, if someone has died, it passes the value 1 to the checker variable and prints that the philo died, consequently the routines will be terminated, because it executes while this variable is not 1. follow my repository: https://github.com/rafalacerda1530/Philosphers
    
- CAPTION
    
    MONITOR = verifies if any philosopher has died
    
    *Numb_meal = number of dishes to eat 
    
    *philo_info() = performs the insertion of philos values in the variables of the Philos struct *main->numb_philos = struct variable that returns quantities of philosophers 
    
    *creates the mutex of each fork = a mutex is a function that blocks the line of code until it is unlocked, so that two threads do not access that code at the same time 
    
    *numb_philo = by 2 in the routine function, it is a logic so that philosophers do not take the forks at the same time. 
    
    ** philo->st_main - >checker != 1 = checker only turns 1 when a philosopher dies, so everyone stops 
    
    * eat = performs the task for the philosopher to eat. 
    
    ate_meal * = variable that checks if each philosopher ate the maximum limit, when it has 
    
    *Join = starts the threads
    
- frame 1
    
    Get_time, takes the current time when it starts to eat, when it finishes it checks the time minus the previous one to know if it has had time
    
    The last parameter is how many times it will eat, it is optional
    
- other
    
    There are several forks for philosophers - only one philosopher eats with two forks at a time-when he finishes eating he puts the forks back and sleeps, when he wakes up he begins to think dnv until he dies of hunger -each philosopher must eat and never die of hunger-philosophers do not talk to each other-philosophers do not know when the other is about to die -no need to say that the philosopher should avoid dying
    
    Comendo
    Não pensam, nem dormem
    Pensando
    Não comem nem dormem
    Dormindo
    Não comem nem pensam
    

https://github.com/Daewoong-Jeon/42Seoul-subject/tree/master/philosophers

https://bigpel66.oopy.io/library/42/inner-circle/9

https://velog.velcdn.com/images%2Fdu0928%2Fpost%2Fee5d8d6a-e585-4e55-867b-9ffd3e315786%2Fimage.png

https://velog.velcdn.com/images%2Fdu0928%2Fpost%2F8f05d284-4201-48bd-9c7a-ef43cf22a8a7%2Fimage.png

https://velog.io/@du0928/Philosophers

https://velog.io/@33bini/Philosophers
