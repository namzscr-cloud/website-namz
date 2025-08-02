<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Namz Shop - Namz Store</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&family=Nunito+Sans:wght@400;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        :root {
            --primary: #6c5ce7;
            --primary-dark: #5649d6;
            --secondary: #0fb9b1;
            --accent: #fd9644;
            --dark: #2d3436;
            --light: #f5f6fa;
        }
        body {
            font-family: 'Poppins', sans-serif;
            background-color: #f9f9f9;
            color: var(--dark);
        }

        .anime-btn {
            background-color: var(--primary);
            color: white;
            border: none;
            padding: 10px 20px;
            border-radius: 5px;
            cursor: pointer;
            transition: all 0.3s;
            position: relative;
            overflow: hidden;
        }

        .anime-btn:hover {
            background-color: var(--primary-dark);
            transform: translateY(-2px);
        }

        .anime-btn:active {
            transform: translateY(0);
        }

        .anime-btn::before {
            content: '';
            position: absolute;
            top: 0;
            left: -100%;
            width: 100%;
            height: 100%;
            background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
            transition: 0.5s;
        }

        .anime-btn:hover::before {
            left: 100%;
        }

        .navbar {
            background-color: white;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .hero {
            background: linear-gradient(rgba(108, 92, 231, 0.8), rgba(108, 92, 231, 0.8)),
            url('na.png') center/cover no-repeat; width: 105%; height: 810px;
            color: white;
        }

        .product-card {
            transition: all 0.3s;
            background-color: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 5px 15px rgba(0,0,0,0.1);
        }

        .product-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 30px rgba(0,0,0,0.2);
        }

        .payment-method {
            transition: all 0.3s;
            border-radius: 8px;
            overflow: hidden;
            background-color: white;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
        }

        .payment-method:hover {
            transform: scale(1.05);
        }

        /* Animation */
        @keyframes float {
            0%, 100% {
                transform: translateY(0);
            }
            50% {
                transform: translateY(-10px);
            }
        }
        .floating {
            animation: float 3s ease-in-out infinite;
        }

        @keyframes fadeIn {
            from {
                opacity: 0;
                transform: translateY(20px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }
        .fade-in {
            animation: fadeIn 1s ease-in-out forwards;
        }

        /* Custom scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }

        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }

        ::-webkit-scrollbar-thumb {
            background: var(--primary);
            border-radius: 10px;
        }
    </style>
</head>
<body class="overflow-x-hidden">
    <nav class="navbar fixed w-full z-50">
        <div class="container mx-auto px-4 py-3 flex justify-between items-center fade-in" style="animation-delay: 0.2s">
            <div class="flex items-center space-x-2">
                <img src="Screenshot 2025-08-02 073143.png" alt="Namz Shop logo - anime-style cat mascot with blue background" class="h-10 w-10 rounded-full">
                <h1 class="text-2xl font-bold text-indigo-600">Namz Shop</h1>
            </div>
            <div class="hidden md:flex space-x-6">
                <a href="#home" class="text-gray-700 hover:text-indigo-600 transition">Home</a>
                <a href="#products" class="text-gray-700 hover:text-indigo-600 transition">Products</a>
                <a href="#about" class="text-gray-700 hover:text-indigo-600 transition">About</a>
                <a href="#contact" class="text-gray-700 hover:text-indigo-600 transition">Contact</a>
            </div>
            <div class="flex items-center space-x-4">
                <button id="cart-btn" class="relative text-gray-700 hover:text-indigo-600">
                    <i class="fas fa-shopping-cart text-xl"></i>
                    <span id="cart-count" class="absolute -top-2 -right-2 bg-indigo-600 text-white text-xs rounded-full h-5 w-5 flex items-center justify-center">0</span>
                </button>
                <button class="md:hidden" id="mobile-menu-button">
                    <i class="fas fa-bars text-xl text-gray-700"></i>
                </button>
            </div>
        </div>
        <div class="hidden md:hidden bg-white w-full pb-4 px-4" id="mobile-menu">
            <a href="#home" class="block py-2 text-gray-700 hover:text-indigo-600 transition">Home</a>
            <a href="#products" class="block py-2 text-gray-700 hover:text-indigo-600 transition">Products</a>
            <a href="#about" class="block py-2 text-gray-700 hover:text-indigo-600 transition">About</a>
            <a href="#contact" class="block py-2 text-gray-700 hover:text-indigo-600 transition">Contact</a>
        </div>
    </nav>

    <section id="home" class="hero py-32 md:py-40 text-center px-4 mt-16 fade-in">
        <div class="container mx-auto">
            <h1 class="text-4xl md:text-6xl font-bold mb-4">Welcome to Namz Shop</h1>
            <p class="text-xl md:text-2xl mb-8 max-w-2xl mx-auto">Welceome everyone You Can buy one of the accounts on this website</p>
            <div class="inline-block relative">
                <a href="#products" id="explore-btn" class="anime-btn inline-block px-8 py-3 text-lg">Explore Products</a>
                <div id="search-container" class="hidden absolute top-full left-1/2 transform -translate-x-1/2 mt-2 w-full md:w-80">
                    <input type="text" id="search-input" placeholder="Search products..." class="w-full px-4 py-2 rounded-lg shadow-md border-gray-300 focus:outline-none focus:ring-2 focus:ring-indigo-500">
                </div>
            </div>
        </div>
    </section>

    <section id="products" class="py-16 bg-gray-50">
        <div class="container mx-auto px-4">
            <h2 class="text-3xl font-bold text-center mb-12">Products</h2>

            <div id="product-list" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-8">
                <div class="product-card product-item">
                    <div class="relative overflow-hidden group">
                        <img src="Screenshot 2025-06-17 200539.png" alt="Limited edition Naruto Shippuden figurine with dynamic action pose" class="w-full h-64 object-cover transition duration-500 group-hover:scale-110">
                        <div class="absolute top-2 right-2 bg-indigo-600 text-white px-2 py-1 text-xs rounded">NEW</div>
                    </div>
                    <div class="p-4">
                        <h3 class="font-semibold text-lg mb-1 product-name">Account Blox Fruit(Roblox)</h3>
                        <p class="text-gray-600 text-sm mb-2">Good Spekk</p>
                        <div class="flex justify-between items-center">
                            <span class="font-bold text-indigo-600 product-price" data-price="60000">Rp.60.000,00</span>
                            <button class="add-to-cart anime-btn px-3 py-1 text-sm" data-id="1" data-name="Account Blox Fruit" data-price="60000" data-image="Screenshot 2025-06-17 200345.png">Add to Cart</button>
                        </div>
                    </div>
                </div>

                <div class="product-card product-item">
                    <div class="relative overflow-hidden group">
                        <img src="roblox fish.jpg" alt="Demon Slayer Kimetsu no Yaiba Nichirin Sword replica with detailed design" class="w-full h-64 object-cover transition duration-500 group-hover:scale-110">
                        <div class="absolute top-2 right-2 bg-red-500 text-white px-2 py-1 text-xs rounded">HOT</div>
                    </div>
                    <div class="p-4">
                        <h3 class="font-semibold text-lg mb-1 product-name">Account fish(Roblox)</h3>
                        <p class="text-gray-600 text-sm mb-2">Spek Gacorr</p>
                        <div class="flex justify-between items-center">
                            <span class="font-bold text-indigo-600 product-price" data-price="60000">Rp.60.000,00</span>
                            <button class="add-to-cart anime-btn px-3 py-1 text-sm" data-id="2" data-name="Account fish" data-price="60000" data-image="roblox fish.jpg">Add to Cart</button>
                        </div>
                    </div>
                </div>

                <div class="product-card product-item">
                    <div class="relative overflow-hidden group">
                        <img src="asep.jpg" alt="Account Blood strike" class="w-full h-64 object-cover transition duration-500 group-hover:scale-110">
                    </div>
                    <div class="p-4">
                        <h3 class="font-semibold text-lg mb-1 product-name">Account Blood strike</h3>
                        <p class="text-gray-600 text-sm mb-2">Spek lumayan</p>
                        <div class="flex justify-between items-center">
                            <span class="font-bold text-indigo-600 product-price" data-price="20000">Rp.20.000,00</span>
                            <button class="add-to-cart anime-btn px-3 py-1 text-sm" data-id="3" data-name="Account Blood strike" data-price="20000" data-image="asep.jpg">Add to Cart</button>
                        </div>
                    </div>
                </div>

                <div class="product-card product-item">
                    <div class="relative overflow-hidden group">
                        <img src="agus.jpg" alt="Account Racing Master" class="w-full h-64 object-cover transition duration-500 group-hover:scale-110">
                    </div>
                    <div class="p-4">
                        <h3 class="font-semibold text-lg mb-1 product-name">Racing Master</h3>
                        <p class="text-gray-600 text-sm mb-2">Spek Mantap</p>
                        <div class="flex justify-between items-center">
                            <span class="font-bold text-indigo-600 product-price" data-price="70000">Rp.70.000,00</span>
                            <button class="add-to-cart anime-btn px-3 py-1 text-sm" data-id="4" data-name="Racing Master" data-price="70000" data-image="agus.jpg">Add to Cart</button>
                        </div>
                    </div>
                </div>
            </div>

            <div class="text-center mt-12">
                <a href="#" class="anime-btn inline-block px-8 py-3">View All Products</a>
            </div>
        </div>
    </section>

    <section id="about" class="py-16 bg-white">
        <div class="container mx-auto px-4">
            <h2 class="text-3xl font-bold text-center mb-12">About Namz Shop</h2>

            <div class="flex flex-col md:flex-row items-center gap-8">
                <div class="md:w-1/2">
                    <img src="https://placehold.co/600x400" alt="Namz Shop storefront with anime merchandise displays and colorful decor" class="w-full rounded-lg shadow-lg floating">
                </div>
                <div class="md:w-1/2">
                    <h3 class="text-2xl font-semibold mb-4">Our Story</h3>
                    <p class="text-gray-700 mb-4">
                        Namz Shop was founded in 2023 with a simple mission: to bring high-quality anime merchandise to fans worldwide.
                        What started as a small passion project has grown into a trusted destination for anime collectors and enthusiasts.
                    </p>
                    <p class="text-gray-700 mb-4">
                        We carefully curate our collection, working directly with Japanese manufacturers and licensed distributors to ensure
                        authenticity and quality in every product we offer.
                    </p>
                    <p class="text-gray-700">
                        Our team consists of die-hard anime fans who understand what collectors want - from rare editions to the latest releases.
                    </p>
                </div>
            </div>
        </div>
    </section>

    <section class="py-16 bg-gray-50">
        <div class="container mx-auto px-4">
            <h2 class="text-3xl font-bold text-center mb-12">Payment Methods</h2>

            <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-5 gap-6">
                <div class="payment-method p-4 text-center">
                    <div class="h-16 flex items-center justify-center">
                        <img src="WhatsApp Image 2025-08-02 at 15.50.29_9749b47e.jpg" alt="Dana" class="max-h-full max-w-full">
                    </div>
                    <h4 class="mt-2 font-medium">Dana</h4>
                    <p class="text-xs text-gray-500 mt-1">Secure Payment</p>
                </div>
                <div class="payment-method p-4 text-center">
                    <div class="h-16 flex items-center justify-center">
                        <img src="WhatsApp Image 2025-08-02 at 16.06.13_0a938e2d.jpg" alt="Gopay" class="max-h-full max-w-full">
                    </div>
                    <h4 class="mt-2 font-medium">Gopay</h4>
                    <p class="text-xs text-gray-500 mt-1">Safe & Easy</p>
                </div>

                <div class="payment-method p-4 text-center">
                    <div class="h-16 flex items-center justify-center">
                        <img src="WhatsApp Image 2025-08-02 at 16.10.05_43d187a3.jpg" alt="Credit card payment icons with anime character illustrations" class="max-h-full max-w-full">
                    </div>
                    <h4 class="mt-2 font-medium">Credit Card</h4>
                    <p class="text-xs text-gray-500 mt-1">Visa, Mastercard</p>
                </div>

                <div class="payment-method p-4 text-center">
                    <div class="h-16 flex items-center justify-center">
                        <img src="WhatsApp Image 2025-08-02 at 16.17.26_e13fe5d6.jpg" alt="Bank transfer" class="max-h-full max-w-full">
                    </div>
                    <h4 class="mt-2 font-medium">Bank Transfer</h4>
                    <p class="text-xs text-gray-500 mt-1">Direct Deposit</p>
                </div>

                <div class="payment-method p-4 text-center">
                    <div class="h-16 flex items-center justify-center">
                        <img src="btc.jpg" alt="Cryptocurrency payment option with anime-style digital currency icons" class="max-h-full max-w-full">
                    </div>
                    <h4 class="mt-2 font-medium">Crypto</h4>
                    <p class="text-xs text-gray-500 mt-1">Bitcoin, Ethereum</p>
                </div>
            </div>
        </div>
    </section>

    <section class="py-16 bg-white">
        <div class="container mx-auto px-4">
            <h2 class="text-3xl font-bold text-center mb-12">What Our Customers Say</h2>

            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="bg-gray-50 p-6 rounded-lg border border-gray-200">
                    <div class="flex items-center mb-4">
                        <img src="https://placehold.co/50x50" alt="Happy female customer Sakura with pink hair anime style" class="w-12 h-12 rounded-full mr-3">
                        <div>
                            <h4 class="font-semibold">Sakura T.</h4>
                            <div class="flex text-yellow-400 text-sm">
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                            </div>
                        </div>
                    </div>
                    <p class="text-gray-700">
                        "The quality of their figures is amazing! I've bought several Naruto items and they're all officially licensed. Super fast shipping too!"
                    </p>
                </div>

                <div class="bg-gray-50 p-6 rounded-lg border border-gray-200">
                    <div class="flex items-center mb-4">
                        <img src="https://placehold.co/50x50" alt="Satisfied male customer Renji with spiky red hair anime style" class="w-12 h-12 rounded-full mr-3">
                        <div>
                            <h4 class="font-semibold">Renji H.</h4>
                            <div class="flex text-yellow-400 text-sm">
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                            </div>
                        </div>
                    </div>
                    <p class="text-gray-700">
                        "NamzPay is so convenient! The payment process makes checkout fun and they always deliver what they promise."
                    </p>
                </div>

                <div class="bg-gray-50 p-6 rounded-lg border border-gray-200">
                    <div class="flex items-center mb-4">
                        <img src="https://placehold.co/50x50" alt="Loyal customer Inoue with cheerful expression anime style" class="w-12 h-12 rounded-full mr-3">
                        <div>
                            <h4 class="font-semibold">Inoue M.</h4>
                            <div class="flex text-yellow-400 text-sm">
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star"></i>
                                <i class="fas fa-star-half-alt"></i>
                            </div>
                        </div>
                    </div>
                    <p class="text-gray-700">
                        "Their customer service is fantastic. I had an issue with sizing on a hoodie and they helped me exchange it quickly with no hassle."
                    </p>
                </div>
            </div>
        </div>
    </section>

    <section id="contact" class="py-16 bg-indigo-50">
        <div class="container mx-auto px-4">
            <h2 class="text-3xl font-bold text-center mb-12">Contact Us</h2>

            <div class="flex flex-col md:flex-row gap-8">
                <div class="md:w-1/2">
                    <h3 class="text-xl font-semibold mb-4">Get in Touch</h3>
                    <p class="text-gray-700 mb-6">
                        Have questions about our products or need support with an order? Our friendly team is here to help!
                    </p>

                    <div class="space-y-4">
                        <div class="flex items-start">
                            <i class="fas fa-map-marker-alt text-indigo-600 mt-1 mr-3"></i>
                            <div>
                                <h4 class="font-medium">Address</h4>
                                <p class="text-gray-700 text-sm">Purbalingga, Babakan </p>
                            </div>
                        </div>

                        <div class="flex items-start">
                            <i class="fas fa-phone-alt text-indigo-600 mt-1 mr-3"></i>
                            <div>
                                <h4 class="font-medium">Phone</h4>
                                <p class="text-gray-700 text-sm">+62 895-0605-6407</p>
                            </div>
                        </div>

                        <div class="flex items-start">
                            <i class="fas fa-envelope text-indigo-600 mt-1 mr-3"></i>
                            <div>
                                <h4 class="font-medium">Email</h4>
                                <p class="text-gray-700 text-sm">support@namz6.com</p>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="md:w-1/2">
                    <form class="bg-white p-6 rounded-lg shadow-sm">
                        <div class="mb-4">
                            <label for="name" class="block text-gray-700 mb-2">Your Name</label>
                            <input type="text" id="name" class="w-full px-4 py-2 border border-gray-300 rounded focus:outline-none focus:border-indigo-600">
                        </div>

                        <div class="mb-4">
                            <label for="email" class="block text-gray-700 mb-2">Email Address</label>
                            <input type="email" id="email" class="w-full px-4 py-2 border border-gray-300 rounded focus:outline-none focus:border-indigo-600">
                        </div>

                        <div class="mb-4">
                            <label for="message" class="block text-gray-700 mb-2">Message</label>
                            <textarea id="message" rows="4" class="w-full px-4 py-2 border border-gray-300 rounded focus:outline-none focus:border-indigo-600"></textarea>
                        </div>

                        <button type="submit" class="anime-btn w-full py-2">Send Message</button>
                    </form>
                </div>
            </div>
        </div>
    </section>

    <footer class="bg-gray-900 text-white py-8">
        <div class="container mx-auto px-4">
            <div class="flex flex-col md:flex-row justify-between items-center">
                <div class="mb-4 md:mb-0">
                    <div class="flex items-center space-x-2">
                        <img src="Screenshot 2025-08-02 073143.png" alt="Namz Shop small logo - anime-style cat mascot" class="h-8 w-8">
                        <h3 class="text-xl font-bold">Namz Shop</h3>
                    </div>
                    <p class="text-gray-400 text-sm mt-2">Games Account</p>
                </div>

                <div class="flex flex-wrap justify-center md:justify-end gap-4 mb-4 md:mb-0">
                    <a href="#" class="text-gray-400 hover:text-white transition">Terms of Service</a>
                    <a href="#" class="text-gray-400 hover:text-white transition">Privacy Policy</a>
                    <a href="#" class="text-gray-400 hover:text-white transition">Shipping Policy</a>
                    <a href="#" class="text-gray-400 hover:text-white transition">Returns</a>
                </div>

                <div class="flex space-x-4">
                    <a href="https://www.facebook.com/share/12MVb6Qao8Z/" class="text-gray-400 hover:text-white text-xl"><i class="fab fa-facebook"></i></a>
                    <a href="https://www.instagram.com/anamfaizkhoirul?igsh=MTIxZXZmNXN3N3Nmaw==" class="text-gray-400 hover:text-white text-xl"><i class="fab fa-instagram"></i></a>
                    <a href="https://www.tiktok.com/@namz_bs?_t=ZS-8yXMCKGbl46&_r=1" class="text-gray-400 hover:text-white text-xl"><i class="fab fa-tiktok"></i></a>
                </div>
            </div>

            <div class="border-t border-gray-800 mt-8 pt-6 text-center text-gray-500 text-sm">
                <p>© 2023 Namz Shop. All rights reserved.</p>
            </div>
        </div>
    </footer>

    <div id="cart-modal" class="fixed inset-0 bg-black bg-opacity-50 z-50 hidden">
        <div class="absolute right-0 top-0 h-full w-full md:w-1/2 lg:w-1/3 bg-white flex flex-col">
            <div class="p-4 border-b flex justify-between items-center">
                <h3 class="text-xl font-bold">Your Cart</h3>
                <button id="close-cart" class="text-gray-500 hover:text-gray-700">
                    <i class="fas fa-times"></i>
                </button>
            </div>

            <div class="flex-grow p-4 overflow-y-auto">
                <div id="cart-items" class="space-y-4">
                    <p class="text-center text-gray-500" id="empty-cart-message">Your cart is empty</p>
                </div>
            </div>

            <div class="border-t p-4">
                <div class="flex justify-between mb-4">
                    <span class="font-semibold">Subtotal:</span>
                    <span id="cart-subtotal">Rp.0,00</span>
                </div>
                <div class="flex justify-between mb-4">
                    <span class="font-semibold">Shipping:</span>
                    <span>Free</span>
                </div>
                <div class="flex justify-between text-xl font-bold mb-6">
                    <span>Total:</span>
                    <span id="cart-total">Rp.0,00</span>
                </div>
                <button id="checkout-btn" class="anime-btn w-full py-3">Proceed to Checkout</button>
            </div>
        </div>
    </div>

    <div id="checkout-modal" class="fixed inset-0 bg-black bg-opacity-50 z-50 hidden">
        <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 bg-white p-6 rounded-lg w-11/12 md:w-2/3 lg:w-1/2 max-h-[80vh] overflow-y-auto">
            <div class="flex justify-between items-center mb-6">
                <h3 class="text-xl font-bold">Complete Your Purchase</h3>
                <button id="close-checkout" class="text-gray-500 hover:text-gray-700">
                    <i class="fas fa-times"></i>
                </button>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div>
                    <h4 class="font-semibold mb-3">Customer Information</h4>
                    <div class="space-y-3">
                        <div>
                            <label class="block text-gray-700 text-sm mb-1">Full Name</label>
                            <input type="text" class="w-full px-3 py-2 border border-gray-300 rounded" placeholder="Your Name">
                        </div>
                        <div>
                            <label class="block text-gray-700 text-sm mb-1">Email</label>
                            <input type="email" class="w-full px-3 py-2 border border-gray-300 rounded" placeholder="your@email.com">
                        </div>
                        <div>
                            <label class="block text-gray-700 text-sm mb-1">Phone</label>
                            <input type="tel" class="w-full px-3 py-2 border border-gray-300 rounded" placeholder="Phone Number">
                        </div>
                    </div>
                </div>

                <div>
                    <h4 class="font-semibold mb-3">Shipping Address</h4>
                    <div class="space-y-3">
                        <div>
                            <label class="block text-gray-700 text-sm mb-1">Address</label>
                            <input type="text" class="w-full px-3 py-2 border border-gray-300 rounded" placeholder="Street Address">
                        </div>
                        <div>
                            <label class="block text-gray-700 text-sm mb-1">City</label>
                            <input type="text" class="w-full px-3 py-2 border border-gray-300 rounded" placeholder="City">
                        </div>
                        <div class="grid grid-cols-2 gap-3">
                            <div>
                                <label class="block text-gray-700 text-sm mb-1">Zip Code</label>
                                <input type="text" class="w-full px-3 py-2 border border-gray-300 rounded" placeholder="Postal Code">
                            </div>
                            <div>
                                <label class="block text-gray-700 text-sm mb-1">Country</label>
                                <select class="w-full px-3 py-2 border border-gray-300 rounded">
                                    <option>Japan</option>
                                    <option>United States</option>
                                    <option>United Kingdom</option>
                                    <option>Canada</option>
                                    <option>Australia</option>
                                </select>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="md:col-span-2">
                    <h4 class="font-semibold mb-3">Payment Method</h4>
                    <div class="space-y-3">
                        <div class="flex items-center justify-between p-3 border border-gray-300 rounded">
                            <div class="flex items-center">
                                <img src="WhatsApp Image 2025-08-02 at 15.50.29_9749b47e.jpg" width="60" alt="Dana" class="mr-3">
                                <span>Dana</span>
                            </div>
                            <input type="radio" name="payment" checked>
                        </div>

                        <div class="flex items-center justify-between p-3 border border-gray-300 rounded">
                            <div class="flex items-center">
                                <img src="WhatsApp Image 2025-08-02 at 16.06.13_0a938e2d.jpg" width="60" alt="Gopay" class="mr-3">
                                <span>Gopay</span>
                            </div>
                            <input type="radio" name="payment">
                        </div>

                        <div class="flex items-center justify-between p-3 border border-gray-300 rounded">
                            <div class="flex items-center">
                                <img src="WhatsApp Image 2025-08-02 at 16.10.05_43d187a3.jpg" width="60" alt="Credit card payment icons" class="mr-3">
                                <span>Credit Card</span>
                            </div>
                            <input type="radio" name="payment">
                        </div>
                        <div class="flex items-center justify-between p-3 border border-gray-300 rounded">
                            <div class="flex items-center">
                                <img src="WhatsApp Image 2025-08-02 at 16.17.26_e13fe5d6.jpg" width="60" alt="Bank Transfer" class="mr-3">
                                <span>Bank Transfer</span>
                            </div>
                            <input type="radio" name="payment">
                        </div>
                        <div class="flex items-center justify-between p-3 border border-gray-300 rounded">
                            <div class="flex items-center">
                                <img src="btc.jpg" width="60" alt="Crypto" class="mr-3">
                                <span>Crypto</span>
                            </div>
                            <input type="radio" name="payment">
                        </div>

                        <div class="flex justify-between items-center mt-6 pt-4 border-t">
                            <span class="font-semibold">Total:</span>
                            <span id="checkout-total" class="text-lg font-bold">Rp.0,00</span>
                        </div>

                        <button id="place-order-btn" class="anime-btn w-full py-3 mt-4">Place Order</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div id="confirmation-modal" class="fixed inset-0 bg-black bg-opacity-50 z-50 hidden">
        <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 bg-white p-8 rounded-lg w-11/12 md:w-1/2 text-center">
            <div class="mb-6">
                <img src="Screenshot 2025-08-02 212841.png" alt="Order confirmation illustration with cute anime character holding a package" class="mx-auto">
            </div>
            <h3 class="text-2xl font-bold mb-4">Thank You For Your Order!</h3>
            <p class="text-gray-700 mb-6">
                Your order has been placed successfully. We've sent a confirmation email to your address.
            </p>
            <button id="close-confirmation" class="anime-btn px-6 py-2">Continue Shopping</button>
        </div>
    </div>

    <script src="https://kit.fontawesome.com/a076d05399.js" crossorigin="anonymous"></script>
    <script>
        document.addEventListener('DOMContentLoaded', () => {
            let cart = {}; // Initialize cart object
            const cartBtn = document.getElementById('cart-btn');
            const cartModal = document.getElementById('cart-modal');
            const closeCartBtn = document.getElementById('close-cart');
            const checkoutModal = document.getElementById('checkout-modal');
            const closeCheckoutBtn = document.getElementById('close-checkout');
            const confirmationModal = document.getElementById('confirmation-modal');
            const closeConfirmationBtn = document.getElementById('close-confirmation');
            const checkoutTotal = document.getElementById('checkout-total');

            // Toggle cart modal
            cartBtn.addEventListener('click', () => {
                cartModal.classList.toggle('hidden');
                updateCart();
            });

            closeCartBtn.addEventListener('click', () => {
                cartModal.classList.add('hidden');
            });

            // Toggle checkout modal
            document.getElementById('checkout-btn').addEventListener('click', () => {
                checkoutModal.classList.remove('hidden');
                updateCheckoutTotal();
            });

            closeCheckoutBtn.addEventListener('click', () => {
                checkoutModal.classList.add('hidden');
            });

            // Close confirmation modal
            closeConfirmationBtn.addEventListener('click', () => {
                confirmationModal.classList.add('hidden');
                cartModal.classList.add('hidden');
                checkoutModal.classList.add('hidden');
                clearCart();
            });

            // Add to cart functionality
            document.querySelectorAll('.add-to-cart').forEach(button => {
                button.addEventListener('click', (e) => {
                    const item = e.target.closest('.product-item');
                    const id = button.dataset.id;
                    const name = button.dataset.name;
                    const price = parseFloat(button.dataset.price);
                    const image = button.dataset.image;

                    addToCart(id, name, price, image);
                    updateCart();
                });
            });

            // Update cart display
            function updateCart() {
                const cartItemsContainer = document.getElementById('cart-items');
                cartItemsContainer.innerHTML = '';
                
                let total = 0;
                let itemCount = 0;

                for (const [id, item] of Object.entries(cart)) {
                    total += item.price * item.quantity;
                    itemCount += item.quantity;

                                    const itemDiv = document.createElement('div');
                                    itemDiv.className = 'flex items-center justify-between p-3 border-b';
                                    // You should continue your cart item rendering logic here...
                                    // For now, let's just show the item name and quantity as a placeholder:
                                    itemDiv.innerHTML = `
                                        <div class="flex items-center">
                                            <img src="${item.image}" alt="${item.name}" class="w-12 h-12 rounded mr-3">
                                            <div>
                                                <div class="font-semibold">${item.name}</div>
                                                <div class="text-sm text-gray-500">Qty: ${item.quantity}</div>
                                            </div>
                                        </div>
                                        <div class="flex flex-col items-end">
                                            <div class="font-bold text-indigo-600">Rp.${(item.price * item.quantity).toLocaleString('id-ID')},00</div>
                                            <button class="remove-item text-red-500 text-xs mt-2" data-id="${id}">Remove</button>
                                        </div>
                                    `;
                                    cartItemsContainer.appendChild(itemDiv);
                                }
                
                                if (itemCount === 0) {
                                    cartItemsContainer.innerHTML = '<p class="text-center text-gray-500" id="empty-cart-message">Your cart is empty</p>';
                                }
                
                                document.getElementById('cart-count').textContent = itemCount;
                                document.getElementById('cart-subtotal').textContent = `Rp.${total.toLocaleString('id-ID')},00`;
                                document.getElementById('cart-total').textContent = `Rp.${total.toLocaleString('id-ID')},00`;
                
                                // Remove item event
                                cartItemsContainer.querySelectorAll('.remove-item').forEach(btn => {
                                    btn.addEventListener('click', (e) => {
                                        const id = btn.dataset.id;
                                        removeFromCart(id);
                                        updateCart();
                                    });
                                });
                            }
                
                            function addToCart(id, name, price, image) {
                                if (cart[id]) {
                                    cart[id].quantity += 1;
                                } else {
                                    cart[id] = { name, price, image, quantity: 1 };
                                }
                            }
                
                            function removeFromCart(id) {
                                if (cart[id]) {
                                    delete cart[id];
                                }
                            }
                
                            function clearCart() {
                                cart = {};
                                updateCart();
                            }
                
                            function updateCheckoutTotal() {
                                let total = 0;
                                for (const item of Object.values(cart)) {
                                    total += item.price * item.quantity;
                                }
                                checkoutTotal.textContent = `Rp.${total.toLocaleString('id-ID')},00`;
                            }
                
                            // Place order button
                            document.getElementById('place-order-btn').addEventListener('click', () => {
                                checkoutModal.classList.add('hidden');
                                confirmationModal.classList.remove('hidden');
                            });
                
                            // Mobile menu toggle
                            const mobileMenuBtn = document.getElementById('mobile-menu-button');
                            const mobileMenu = document.getElementById('mobile-menu');
                            mobileMenuBtn.addEventListener('click', () => {
                                mobileMenu.classList.toggle('hidden');
                            });
                
                            // Optional: Add search bar toggle
                            const exploreBtn = document.getElementById('explore-btn');
                            const searchContainer = document.getElementById('search-container');
                            if (exploreBtn && searchContainer) {
                                exploreBtn.addEventListener('click', (e) => {
                                    e.preventDefault();
                                    searchContainer.classList.toggle('hidden');
                                    if (!searchContainer.classList.contains('hidden')) {
                                        document.getElementById('search-input').focus();
                                    }
                                });
                            }
                        });
                    </script># website-namz
Websitw
