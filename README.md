Share

User
You said:
import React, { useState } from "react";
import { Button } from "@/components/ui/button";
import { Card, CardContent } from "@/components/ui/card";
import { ShoppingCart, CheckCircle, User } from "lucide-react";
import { useRouter } from "next/router";

const productNames = [
  "Luxury Heart Pendant",
  "Couple Promise Rings",
  "LED Rose Dome",
  "Personalized Name Bracelet",
  "Magnetic Couple Bracelets",
  "3D Moon Lamp"
];

const products = Array.from({ length: 100 }, (_, i) => {
  const randomIndex = Math.floor(Math.random() * productNames.length);
  return {
    id: i + 1,
    name: ${productNames[randomIndex]} ${i + 1},
    price: ${799 + (i % 5) * 100},
    image: "https://via.placeholder.com/300",
    description: Exclusive high-end product: ${productNames[randomIndex]}. Perfect for couples!,
    link: https://yourshopify.com/product${i + 1},
  };
});

export default function HomePage() {
  const [cartMessage, setCartMessage] = useState("");
  const [cart, setCart] = useState([]);
  const router = useRouter();

  const addToCart = (product) => {
    setCart([...cart, product]);
    setCartMessage(${product.name} added to cart!);
    setTimeout(() => setCartMessage(""), 3000); // Hide message after 3 seconds
  };

  const navigateToProductDetails = (productId) => {
    router.push(/product/${productId});
  };

  return (
    <div className="min-h-screen bg-gradient-to-br from-pink-50 to-purple-100 text-gray-900 p-6 relative overflow-auto">
      {/* Header */}
      <header className="text-center text-6xl font-extrabold mb-10 uppercase tracking-widest font-cinzel text-transparent bg-clip-text bg-gradient-to-r from-pink-600 to-purple-600 relative">
        NORHAM LUXE
        <div className="absolute top-0 right-5 flex items-center space-x-4">
          <div 
            className="bg-white p-2 rounded-full cursor-pointer hover:shadow-lg transition-shadow"
            onClick={() => router.push('/login')}
          >
            <User className="text-pink-700" size={24} />
          </div>
        </div>
      </header>

      {/* Cart Success Message */}
      {cartMessage && (
        <div className="fixed top-5 left-1/2 transform -translate-x-1/2 bg-green-600 text-white px-4 py-2 rounded-lg shadow-md flex items-center animate-fade-in">
          <CheckCircle className="mr-2" size={20} /> {cartMessage}
        </div>
      )}

      {/* Product Grid */}
      <div className="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-6 overflow-y-auto max-h-[80vh] p-4">
        {products.map((product) => (
          <Card 
            key={product.id} 
            className="p-4 shadow-2xl rounded-2xl bg-white hover:shadow-3xl transition-shadow duration-300"
          >
            <CardContent className="flex flex-col items-center text-center">
              <img 
                src={product.image} 
                alt={product.name} 
                className="w-40 h-40 object-cover rounded-full border-4 border-pink-200 shadow-lg cursor-pointer hover:border-pink-400 transition-all"
                onClick={() => navigateToProductDetails(product.id)}
              />
              <h2 className="text-xl font-semibold mt-4 text-pink-600">{product.name}</h2>
              <p className="text-sm text-gray-600 px-2 mt-2">{product.description}</p>
              <div className="flex justify-between items-center mt-4 w-full">
                <span className="text-lg font-bold text-purple-800">₹{product.price}</span>
                <Button 
                  className="bg-gradient-to-r from-pink-600 to-purple-600 text-white px-4 py-2 rounded-lg hover:from-pink-700 hover:to-purple-700 transition-all"
                  onClick={() => addToCart(product)}
                >
                  <ShoppingCart className="mr-2" size={18} /> Buy Now
                </Button>
              </div>
            </CardContent>
          </Card>
        ))}
      </div>
    </div>
  );
}# NORHAM-LUXE
Dropshipping 
