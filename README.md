# Train_Reservation_system
# 🚆 Railway Reservation System using Multithreading (C++)

## 📖 Overview

This project is a **Multithreaded Railway Reservation System** implemented in **C++** using the Standard Thread Library. It simulates multiple users performing railway reservation operations simultaneously while ensuring safe and synchronized access to shared resources.

The project demonstrates the practical use of **threads**, **mutexes**, and **condition variables** to efficiently handle concurrent operations without data inconsistency.

---

## ✨ Features

* 🚆 Simulates **100 trains**, each with an initial capacity of **500 seats**.
* 👥 Creates **20 worker threads**, each representing an independent user.
* 🔍 Supports the following operations:

  * **Seat Inquiry** – Displays the number of available seats.
  * **Seat Booking** – Books a random number of seats (**5–10**) if available.
  * **❌ Booking Cancellation** – Cancels a random number of previously booked seats.
* 🎲 Randomly generates train numbers and operations to simulate real-world concurrent requests.
* 📊 Displays the final reservation chart showing the available seats for every train after the simulation.

---

## ⚙️ Working

Each worker thread repeatedly performs the following steps:

1. ⏳ Sleeps for a random duration.
2. 🚆 Selects a random train.
3. 🎯 Randomly chooses one of the three operations:

   * 🔍 Inquiry
   * 🎟️ Booking
   * ❌ Cancellation
4. ⏸️ Waits if the maximum number of active queries has been reached or if a conflicting booking request is already in progress.
5. ✅ Executes the operation and updates the seat count when required.
6. 🔔 Removes itself from the active query list and notifies waiting threads.

The simulation runs for the configured time and finally prints the reservation status of all trains.

---

## 🔒 Synchronization

The project uses the following synchronization mechanisms:

* 🧵 **std::thread** – Executes multiple reservation requests concurrently.
* 🔐 **std::mutex**

  * `query_mutex` protects the shared list of active queries.
  * `print_mutex` ensures clean and non-overlapping console output.
* 🔄 **std::condition_variable**

  * Suspends threads when the maximum number of active queries has been reached.
  * Prevents conflicting booking operations on the same train from executing simultaneously.

---

## 🛠️ Technologies Used

* 💻 C++
* 🧵 `std::thread`
* 🔐 `std::mutex`
* 🔄 `std::condition_variable`
* ⏱️ `std::chrono`

---

## 🎯 Learning Outcomes

* 🧵 Multithreading in C++
* 🔒 Thread synchronization using mutexes
* 🔄 Thread coordination using condition variables
* 🛡️ Safe access to shared resources
* 🚆 Simulation of a concurrent railway reservation system
