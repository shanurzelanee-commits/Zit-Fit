
import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";

export default function ZitFitWebsite() {
  const [filter, setFilter] = useState("all");

  const whatsappNumber = "8801864279528";
  const whatsappLink = `https://wa.me/${whatsappNumber}`;

  const products = [
    { name: "Basic T-Shirt", price: 8, category: "low" },
    { name: "Casual Shirt", price: 15, category: "low" },
    { name: "Premium Jacket", price: 60, category: "high" },
    { name: "Designer Hoodie", price: 75, category: "high" },
  ];

  const filtered = products.filter((p) => {
    if (filter === "all") return true;
    return p.category === filter;
  });

  return (
    <div className="min-h-screen bg-gray-50 text-gray-900">
      {/* Navbar */}
      <nav className="flex justify-between items-center p-4 bg-black text-white">
        <h1 className="text-2xl font-bold">🧵 Zit-Fit</h1>
        <div className="space-x-4">
          <a href="#products">Products</a>
          <a href="#custom">Custom Orders</a>
          <a href="#contact">Contact</a>
        </div>
      </nav>

      {/* Hero */}
      <section className="text-center py-16 bg-white">
        <h2 className="text-4xl font-bold mb-4">Zit-Fit Clothing Store</h2>
        <p className="text-gray-600">
          Affordable fashion + premium custom clothing tailored for you
        </p>
        <a
          href={whatsappLink}
          target="_blank"
          rel="noreferrer"
        >
          <Button className="mt-4 bg-green-500 hover:bg-green-600">
            Chat on WhatsApp
          </Button>
        </a>
      </section>

      {/* Products */}
      <section id="products" className="p-6">
        <h2 className="text-3xl font-bold mb-4">Our Products</h2>

        <div className="flex gap-3 mb-4">
          <Button onClick={() => setFilter("all")}>All</Button>
          <Button onClick={() => setFilter("low")}>Low Price</Button>
          <Button onClick={() => setFilter("high")}>High Price</Button>
        </div>

        <div className="grid md:grid-cols-2 gap-4">
          {filtered.map((item, i) => (
            <Card key={i}>
              <CardContent className="p-4">
                <h3 className="text-xl font-semibold">{item.name}</h3>
                <p className="text-green-600 font-medium">Price: ${item.price}</p>
                <p className="text-sm text-gray-500">
                  Category: {item.category === "low" ? "Low Price" : "Premium"}
                </p>
                <a href={whatsappLink} target="_blank" rel="noreferrer">
                  <Button className="mt-3 bg-black text-white">
                    Order on WhatsApp
                  </Button>
                </a>
              </CardContent>
            </Card>
          ))}
        </div>
      </section>

      {/* Custom Section */}
      <section id="custom" className="p-6 bg-white">
        <h2 className="text-3xl font-bold mb-4">Custom Clothing Orders</h2>
        <p className="mb-4 text-gray-600">
          Get fully customized outfits made according to your design, size, and style.
        </p>

        <form className="grid gap-3 max-w-md">
          <input className="border p-2" placeholder="Your Name" />
          <input className="border p-2" placeholder="Clothing Type" />
          <input className="border p-2" placeholder="Design Description" />
          <Button type="button" className="bg-green-500">
            Send Request
          </Button>
        </form>

        <p className="mt-4 text-sm text-gray-500">
          After sending request, contact us directly on WhatsApp for faster response.
        </p>
      </section>

      {/* Contact */}
      <section id="contact" className="p-6">
        <h2 className="text-3xl font-bold mb-4">Contact Us</h2>

        <p className="mb-2">📞 WhatsApp: 01864279528</p>
        <a href={whatsappLink} target="_blank" rel="noreferrer">
          <Button className="bg-green-500 mb-4">Open WhatsApp Chat</Button>
        </a>

        <p className="mb-4">Email: zitfit@example.com</p>

        <div className="mb-4">
          <h3 className="font-semibold mb-2">Our Location</h3>
          <iframe
            title="Zit-Fit Location"
            className="w-full h-64 border"
            src="https://www.google.com/maps/embed?pb=!1m18!"
          ></iframe>
        </div>
      </section>

      {/* Footer */}
      <footer className="text-center p-4 bg-black text-white">
        © {new Date().getFullYear()} Zit-Fit Clothing. All rights reserved.
      </footer>
    </div>
  );
}
