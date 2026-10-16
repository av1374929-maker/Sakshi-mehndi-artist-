
"use strict";

// Apna WhatsApp number country code ke saath likhein.
// Example: 91 ke baad 10 digit mobile number.
// Filhaal demo number hai; ise apne asli number se badlein.
const WHATSAPP_NUMBER = "91XXXXXXXXXX";

const menuBtn = document.getElementById("menuBtn");
const navbar = document.getElementById("navbar");
const bookingForm = document.getElementById("bookingForm");
const whatsappFloat = document.getElementById("whatsappFloat");

// Mobile navigation
menuBtn.addEventListener("click", function () {
  const isOpen = navbar.classList.toggle("active");
  menuBtn.setAttribute("aria-expanded", String(isOpen));
  menuBtn.textContent = isOpen ? "✕" : "☰";
});

// Click karne par menu band
navbar.querySelectorAll("a").forEach(function (link) {
  link.addEventListener("click", function () {
    navbar.classList.remove("active");
    menuBtn.setAttribute("aria-expanded", "false");
    menuBtn.textContent = "☰";
  });
});

// WhatsApp number verify karein
function isWhatsAppConfigured() {
  return /^[1-9]\d{10,14}$/.test(WHATSAPP_NUMBER);
}

// WhatsApp message bhejne ke liye URL
function openWhatsApp(message) {
  if (!isWhatsAppConfigured()) {
    alert(
      "Pehle script.js mein WHATSAPP_NUMBER ko apne sahi number se badlein."
    );
    return;
  }

  const url =
    "https://wa.me/" + WHATSAPP_NUMBER +
    "?text=" + encodeURIComponent(message);

  window.open(url, "_blank", "noopener,noreferrer");
}

// Floating WhatsApp button
whatsappFloat.addEventListener("click", function (event) {
  event.preventDefault();
  openWhatsApp(
    "Namaste Sakshi Mehndi Artist! Mujhe mehndi booking ke baare mein jaankari chahiye."
  );
});

// Booking form
bookingForm.addEventListener("submit", function (event) {
  event.preventDefault();

  if (!bookingForm.reportValidity()) return;

  const name = document.getElementById("customerName").value.trim();
  const phone = document.getElementById("customerPhone").value.trim();
  const service = document.getElementById("serviceType").value;
  const date = document.getElementById("eventDate").value;
  const details = document.getElementById("customerMessage").value.trim();

  const message =
    "Namaste Sakshi Mehndi Artist!\n\n" +
    "Mujhe appointment book karna hai.\n\n" +
    "Name: " + name + "\n" +
    "Phone: " + phone + "\n" +
    "Service: " + service + "\n" +
    "Event Date: " + date + "\n" +
    "Additional Details: " + (details || "Not provided") + "\n\n" +
    "Kripya booking aur price ki jaankari dein.";

  openWhatsApp(message);
});

// Past dates ko select karne se rokna
const eventDate = document.getElementById("eventDate");
const today = new Date();
const localDate =
  today.getFullYear() + "-" +
  String(today.getMonth() + 1).padStart(2, "0") + "-" +
  String(today.getDate()).padStart(2, "0");

eventDate.min = localDate;

// Footer year
document.getElementById("year").textContent =
  new Date().getFullYear();
