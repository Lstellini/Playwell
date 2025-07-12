# Playwell
import React, { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Menu, X } from "lucide-react";

export default function Website() {
  const [menuOpen, setMenuOpen] = useState(false);
  const [showForm, setShowForm] = useState(false);

  const toggleMenu = () => setMenuOpen(!menuOpen);
  const openForm = (source) => {
    console.log(`Quote requested from: ${source}`);
    setShowForm(true);
  };
  const closeForm = () => setShowForm(false);

  return (
    <div className="font-sans text-gray-800">
      {/* Navbar */}
      <nav className="bg-white shadow-md sticky top-0 z-50">
        <div className="max-w-7xl mx-auto px-4 py-4 flex justify-between items-center">
          <h1 className="text-2xl font-bold text-blue-800">Playwell</h1>
          <div className="md:hidden" onClick={toggleMenu}>
            {menuOpen ? <X /> : <Menu />}
          </div>
          <ul className="hidden md:flex space-x-6 text-blue-800 font-semibold">
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#equipment">Play Equipment</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        </div>
        {menuOpen && (
          <ul className="md:hidden px-4 pb-4 space-y-2 bg-white text-blue-800">
            <li><a href="#home">Home</a></li>
            <li><a href="#about">About</a></li>
            <li><a href="#services">Services</a></li>
            <li><a href="#equipment">Play Equipment</a></li>
            <li><a href="#contact">Contact</a></li>
          </ul>
        )}
      </nav>

      {/* Hero Section */}
      <section id="home" className="bg-blue-100 text-center py-20 px-4">
        <h2 className="text-4xl font-bold text-blue-800 mb-4">Designing Creative Play Spaces</h2>
        <p className="text-lg mb-6">Custom outdoor play areas that inspire imagination and adventure.</p>
        <div className="flex justify-center gap-4">
          <Button className="bg-blue-800 hover:bg-blue-700 text-white">Explore Now</Button>
          <Button variant="outline" className="border-blue-800 text-blue-800 hover:bg-blue-200" onClick={() => openForm("Hero Section")}>Request a Quote</Button>
        </div>
      </section>

      {/* About Section */}
      <section id="about" className="py-20 px-4 max-w-5xl mx-auto">
        <h3 className="text-3xl font-bold text-center text-blue-800 mb-8">About Us</h3>
        <p className="text-lg text-center text-gray-700">
          At Playwell, we specialise in creating play spaces that encourage physical activity, social interaction and creativity for children of all ages. Our team works closely with clients to bring each vision to life with safe, innovative and fun solutions.
        </p>
      </section>

      {/* Services Section */}
      <section id="services" className="bg-gray-50 py-20 px-4">
        <h3 className="text-3xl font-bold text-center text-blue-800 mb-12">Our Services</h3>
        <div className="grid md:grid-cols-3 gap-6 max-w-6xl mx-auto">
          {['Design Consultation', 'Installation', 'Maintenance'].map((service, index) => (
            <Card key={index} className="shadow-md">
              <CardContent className="p-6 text-center">
                <h4 className="text-xl font-semibold mb-2 text-blue-700">{service}</h4>
                <p className="text-gray-600">Professional {service.toLowerCase()} tailored to your play space needs.</p>
              </CardContent>
            </Card>
          ))}
        </div>
        <div className="text-center mt-10">
          <Button className="bg-blue-800 hover:bg-blue-700 text-white" onClick={() => openForm("Services Section")}>Request a Free Quote</Button>
        </div>
      </section>

      {/* Play Equipment Section */}
      <section id="equipment" className="py-20 px-4 max-w-6xl mx-auto">
        <h3 className="text-3xl font-bold text-center text-blue-800 mb-12">Play Equipment</h3>
        <div className="grid md:grid-cols-3 gap-6">
          {['Climbing Frames', 'Slides & Swings', 'Nature Play'].map((item, index) => (
            <Card key={index} className="shadow-md">
              <CardContent className="p-6 text-center">
                <h4 className="text-xl font-semibold mb-2 text-blue-700">{item}</h4>
                <p className="text-gray-600">High-quality and safe equipment perfect for outdoor environments.</p>
              </CardContent>
            </Card>
          ))}
        </div>
        <div className="text-center mt-10">
          <Button className="bg-blue-800 hover:bg-blue-700 text-white" onClick={() => openForm("Equipment Section")}>Get a Quote</Button>
        </div>
      </section>

      {/* Contact Modal */}
      {showForm && (
        <div className="fixed inset-0 bg-black bg-opacity-50 flex justify-center items-center z-50">
          <div className="bg-white p-8 rounded-lg max-w-md w-full relative">
            <button className="absolute top-2 right-2 text-gray-600" onClick={closeForm}>&times;</button>
            <h3 className="text-2xl font-bold text-blue-800 mb-6 text-center">Request a Quote</h3>
            <form className="space-y-6">
              <div>
                <label className="block text-sm font-medium text-gray-700">Name</label>
                <input type="text" className="mt-1 w-full border border-gray-300 rounded-md p-2" required />
              </div>
              <div>
                <label className="block text-sm font-medium text-gray-700">Email</label>
                <input type="email" className="mt-1 w-full border border-gray-300 rounded-md p-2" required />
              </div>
              <div>
                <label className="block text-sm font-medium text-gray-700">Message</label>
                <textarea rows="4" className="mt-1 w-full border border-gray-300 rounded-md p-2" required></textarea>
              </div>
              <Button type="submit" className="bg-blue-800 hover:bg-blue-700 text-white w-full">Send Request</Button>
            </form>
          </div>
        </div>
      )}

      {/* Footer */}
      <footer className="bg-blue-800 text-white text-center py-6 mt-10">
        <p>&copy; {new Date().getFullYear()} Playwell. All rights reserved.</p>
      </footer>
    </div>
  );
}
