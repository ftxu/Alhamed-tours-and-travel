// NOTE: To simplify deployment, the custom 'ui/button', 'ui/card' etc., imports 
// have been replaced with internal component definitions that use standard HTML 
// elements and Tailwind classes.

import { useState } from "react";

const AlhamedToursTravels = () => {
  const [activeTab, setActiveTab] = useState('all');
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');
  const [message, setMessage] = useState('');
  const [isSubmitted, setIsSubmitted] = useState(false);

  // WhatsApp Link Setup
  const whatsappNumber = "966504643552"; // Full international format without '+' or '00'
  const bookNowMessage = "I'd like to know more about booking a trip with Alhamed Tours & Travels";
  const encodedBookNowMessage = encodeURIComponent(bookNowMessage);
  const whatsappLink = `https://wa.me/${whatsappNumber}?text=${encodedBookNowMessage}`;

  const handleSubmit = (e: React.FormEvent) => {
    e.preventDefault();
    // In a real application, this would send the form data to a server
    setIsSubmitted(true);
    setName('');
    setEmail('');
    setMessage('');
  };

  // Simplified Component definitions for deployment
  const Card = ({ children, className }: { children: React.ReactNode, className?: string }) => (
    <div className={`bg-white p-6 rounded-lg shadow-md ${className}`}>
      {children}
    </div>
  );
  const CardHeader = ({ children }: { children: React.ReactNode }) => <div className="mb-4">{children}</div>;
  const CardTitle = ({ children, className }: { children: React.ReactNode, className?: string }) => <h3 className={`text-xl font-semibold ${className}`}>{children}</h3>;
  const CardDescription = ({ children }: { children: React.ReactNode }) => <p className="text-sm text-gray-500">{children}</p>;
  const CardContent = ({ children }: { children: React.ReactNode }) => <div className="text-gray-700">{children}</div>;
  const CardFooter = ({ children }: { children: React.ReactNode }) => <div className="mt-4">{children}</div>;
  const Button = ({ children, className, variant, onClick }: { children: React.ReactNode, className?: string, variant?: string, onClick?: () => void }) => (
    <button 
      onClick={onClick}
      className={`px-6 py-2 rounded-lg font-medium transition-colors ${className} ${variant === 'outline' ? 'border border-white text-white hover:bg-blue-800' : 'bg-blue-600 hover:bg-blue-700 text-white'}`}
    >
      {children}
    </button>
  );
  
  const hotels = {
    jeddah: [
      { name: "Jeddah Hilton", description: "Luxury accommodations with stunning Red Sea views", price: "SAR 850/night" },
      { name: "Park Hyatt Jeddah", description: "5-star hotel with private beach access", price: "SAR 1200/night" },
      { name: "Radisson Blu Hotel", description: "Modern hotel in the heart of Jeddah", price: "SAR 700/night" },
      { name: "InterContinental Jeddah", description: "Elegant waterfront property with premium amenities", price: "SAR 950/night" },
      { name: "Rosewood Jeddah", description: "Luxury hotel with exceptional service and facilities", price: "SAR 1100/night" }
    ],
    makkah: [
      { name: "Makkah Clock Royal Tower", description: "Iconic hotel overlooking the Grand Mosque", price: "SAR 1500/night" },
      { name: "Swissôtel Makkah", description: "Luxury accommodations steps from Haram", price: "SAR 1300/night" },
      { name: "Fairmont Makkah", description: "5-star hotel with breathtaking mosque views", price: "SAR 1400/night" },
      { name: "Hilton Suites Makkah", description: "Spacious suites perfect for families", price: "SAR 1200/night" },
      { name: "Movenpick Hotel & Residences", description: "Comfortable stay with Haram proximity", price: "SAR 1000/night" }
    ],
    dubai: [
      { name: "Burj Al Arab Jumeirah", description: "Iconic 7-star hotel with unmatched luxury", price: "$1500/night" },
      { name: "Atlantis The Palm", description: "Resort experience with waterpark and marine habitats", price: "$800/night" },
      { name: "Armani Hotel Dubai", description: "Sophisticated stays in the Burj Khalifa", price: "$1200/night" },
      { name: "Jumeirah Beach Hotel", description: "Beachfront luxury with stunning views", price: "$700/night" },
      { name: "The Ritz-Carlton Dubai", description: "Elegant resort with private beach access", price: "$900/night" }
    ],
    worldwide: [
      { name: "The Plaza Hotel, New York", description: "Historic luxury hotel facing Central Park", price: "$1200/night" },
      { name: "Hotel de Crillon, Paris", description: "18th-century palace with timeless elegance", price: "$1100/night" },
      { name: "The Savoy, London", description: "Iconic British luxury on the Strand", price: "$1000/night" },
      { name: "Four Seasons Bali", description: "Tropical paradise with private villas", price: "$800/night" },
      { name: "Taj Lake Palace, Udaipur", description: "Floating palace on Lake Pichola", price: "$600/night" }
    ]
  };
  const packages = [
    { name: "Hajj Package", description: "Complete spiritual journey with expert guidance", duration: "15 days", price: "Starting at SAR 15,000" },
    { name: "Umrah Package", description: "Sacred pilgrimage with comfortable accommodations", duration: "7-10 days", price: "Starting at SAR 5,000" },
    { name: "Family Vacation", description: "Memorable trips for families worldwide", duration: "Customizable", price: "Tailored packages" },
    { name: "Business Travel", description: "Seamless corporate travel solutions", duration: "As required", price: "Competitive rates" }
  ];
  return (
    <div className="min-h-screen bg-gradient-to-b from-blue-50 to-white">
      {/* Header */}
      <header className="bg-white shadow-sm sticky top-0 z-50">
        <div className="container mx-auto px-4 py-4 flex justify-between items-center">
          <div className="flex items-center space-x-2">
            <div className="w-10 h-10 bg-blue-600 rounded-full flex items-center justify-center">
              <span className="text-white font-bold text-lg">A</span>
            </div>
            <h1 className="text-2xl font-bold text-blue-800">Alhamed Tours & Travels</h1>
          </div>
          <nav className="hidden md:flex space-x-8">
            <a href="#home" className="text-blue-700 hover:text-blue-900 font-medium">Home</a>
            <a href="#about" className="text-blue-700 hover:text-blue-900 font-medium">About</a>
            <a href="#services" className="text-blue-700 hover:text-blue-900 font-medium">Services</a>
            <a href="#hotels" className="text-blue-700 hover:text-blue-900 font-medium">Hotels</a>
            <a href="#contact" className="text-blue-700 hover:text-blue-900 font-medium">Contact</a>
          </nav>
          {/* UPDATED: Book Now button with WhatsApp link */}
          <a href={whatsappLink} target="_blank" rel="noopener noreferrer">
            <Button className="bg-blue-600 hover:bg-blue-700 text-white">Book Now</Button>
          </a>
        </div>
      </header>

      {/* Hero Section */}
      <section id="home" className="bg-blue-900 text-white py-20">
        <div className="container mx-auto px-4 text-center">
          <h2 className="text-4xl md:text-6xl font-bold mb-4">Your Journey Begins Here</h2>
          <p className="text-xl md:text-2xl mb-8 max-w-3xl mx-auto">
            Experience premium travel services with Alhamed Tours & Travels - Your trusted partner for Hajj, Umrah, and worldwide adventures.
          </p>
          <div className="flex flex-col md:flex-row justify-center gap-4">
            {/* UPDATED: Explore Packages button with WhatsApp link */}
            <a href={whatsappLink} target="_blank" rel="noopener noreferrer">
              <Button className="bg-white text-blue-900 hover:bg-blue-100 text-lg px-8 py-3">Explore Packages</Button>
            </a>
            <a href="#contact">
              <Button variant="outline" className="border-white text-white hover:bg-blue-800 text-lg px-8 py-3">Contact Us</Button>
            </a>
          </div>
        </div>
      </section>

      {/* About Section */}
      <section id="about" className="py-16 bg-white">
        <div className="container mx-auto px-4">
          <div className="text-center mb-12">
            <h2 className="text-3xl md:text-4xl font-bold text-blue-800 mb-4">About Alhamed Tours & Travels</h2>
            <p className="text-lg text-gray-600 max-w-3xl mx-auto">
              With years of experience in the travel industry, we specialize in creating unforgettable journeys for pilgrims and travelers alike.
              Our licensed services ensure you have a seamless and spiritually enriching experience.
            </p>
          </div>
          <div className="grid md:grid-cols-3 gap-8">
            <Card>
              <CardHeader>
                <CardTitle className="text-blue-700">Expert Guidance</CardTitle>
              </CardHeader>
              <CardContent>
                <p>Our team of experienced guides ensures your spiritual journey is meaningful and hassle-free.</p>
              </CardContent>
            </Card>
            <Card>
              <CardHeader>
                <CardTitle className="text-blue-700">Premium Accommodations</CardTitle>
              </CardHeader>
              <CardContent>
                <p>We partner with the finest hotels worldwide to provide comfort during your travels.</p>
              </CardContent>
            </Card>
            <Card>
              <CardHeader>
                <CardTitle className="text-blue-700">24/7 Support</CardTitle>
              </CardHeader>
              <CardContent>
                <p>Round-the-clock assistance to address any concerns during your journey.</p>
              </CardContent>
            </Card>
          </div>
        </div>
      </section>

      {/* Services Section */}
      <section id="services" className="py-16 bg-blue-50">
        <div className="container mx-auto px-4">
          <div className="text-center mb-12">
            <h2 className="text-3xl md:text-4xl font-bold text-blue-800 mb-4">Our Services</h2>
            <p className="text-lg text-gray-600 max-w-3xl mx-auto">
              From spiritual journeys to luxury vacations, we offer comprehensive travel solutions tailored to your needs.
            </p>
          </div>
          <div className="grid md:grid-cols-2 lg:grid-cols-4 gap-6">
            {packages.map((pkg, index) => (
              <Card key={index} className="hover:shadow-lg transition-shadow">
                <CardHeader>
                  <CardTitle className="text-blue-700">{pkg.name}</CardTitle>
                  <CardDescription>{pkg.duration}</CardDescription>
                </CardHeader>
                <CardContent>
                  <p className="mb-4">{pkg.description}</p>
                  <p className="font-semibold text-blue-600">{pkg.price}</p>
                </CardContent>
                <CardFooter>
                  {/* UPDATED: Learn More button with WhatsApp link and airplane icon */}
                  <a href={whatsappLink} target="_blank" rel="noopener noreferrer" className="w-full">
                    <Button className="w-full bg-blue-600 hover:bg-blue-700 flex items-center justify-center">
                      <svg
                        xmlns="http://www.w3.org/2000/svg"
                        className="h-5 w-5 mr-2 -rotate-45 transform"
                        fill="none"
                        viewBox="0 0 24 24"
                        stroke="currentColor"
                        strokeWidth={2}
                      >
                        <path
                          strokeLinecap="round"
                          strokeLinejoin="round"
                          d="M12 19l9 2-9-18-9 18 9-2zm0 0v-8"
                        />
                      </svg>
                      Learn More
                    </Button>
                  </a>
                </CardFooter>
              </Card>
            ))}
          </div>
        </div>
      </section>

      {/* Hotels Section */}
      <section id="hotels" className="py-16 bg-white">
        <div className="container mx-auto px-4">
          <div className="text-center mb-12">
            <h2 className="text-3xl md:text-4xl font-bold text-blue-800 mb-4">Premium Hotel Partners</h2>
            <p className="text-lg text-gray-600 max-w-3xl mx-auto">
              We collaborate with top hotels worldwide to ensure your comfort and satisfaction.
            </p>
          </div>
          
          <div className="mb-8 flex overflow-x-auto pb-4 space-x-2">
            <Button 
              variant={activeTab === 'all' ? 'default' : 'outline'} 
              onClick={() => setActiveTab('all')}
              className="whitespace-nowrap bg-blue-600 text-white" 
            >
              All Hotels
            </Button>
            <Button 
              variant={activeTab === 'jeddah' ? 'default' : 'outline'} 
              onClick={() => setActiveTab('jeddah')}
              className="whitespace-nowrap bg-blue-600 text-white" 
            >
              Jeddah
            </Button>
            <Button 
              variant={activeTab === 'makkah' ? 'default' : 'outline'} 
              onClick={() => setActiveTab('makkah')}
              className="whitespace-nowrap bg-blue-600 text-white" 
            >
              Makkah
            </Button>
            <Button 
              variant={activeTab === 'dubai' ? 'default' : 'outline'} 
              onClick={() => setActiveTab('dubai')}
              className="whitespace-nowrap bg-blue-600 text-white" 
            >
              Dubai
            </Button>
            <Button 
              variant={activeTab === 'worldwide' ? 'default' : 'outline'} 
              onClick={() => setActiveTab('worldwide')}
              className="whitespace-nowrap bg-blue-600 text-white" 
            >
              Worldwide
            </Button>
          </div>

          
          {/* Hotels Grid */}
          <div className="grid md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-5 gap-6">
            {/* Jeddah Hotels */}
            {activeTab === 'all' || activeTab === 'jeddah' ? (
              <>
                <Card className="overflow-hidden">
                  <div className="h-48 bg-blue-100 flex items-center justify-center">
                    <img 
                      src="https://placeholder-image-service.onrender.com/image/300x200?prompt=Luxury hotel exterior with modern architecture and palm trees&id=jd1" 
                      alt="Modern luxury hotel building with contemporary design and landscape" 
                      className="w-full h-full object-cover"
                    />
                  </div>
                  <CardHeader>
                    <CardTitle className="text-lg">Jeddah Hilton</CardTitle>
                  </CardHeader>
                  <CardContent>
                    <p className="text-sm text-gray-600 mb-2">Luxury accommodations with stunning Red Sea views</p>
                    <p className="font-semibold text-blue-600">SAR 850/night</p>
                  </CardContent>
                </Card>
                
                <Card className="overflow-hidden">
                  <div className="h-48 bg-blue-100 flex items-center justify-center">
                    <img 
                      src="https://placeholder-image-service.onrender.com/image/300x200?prompt=Elegant hotel with private beach and luxury amenities&id=jd2" 
                      alt="Upscale hotel with beachfront property and luxury facilities" 
                      className="w-full h-full object-cover"
                    />
                  </div>
                  <CardHeader>
                    <CardTitle className="text-lg">Park Hyatt Jeddah</CardTitle>
                  </CardHeader>
                  <CardContent>
                    <p className="text-sm text-gray-600 mb-2">5-star hotel with private beach access</p>
                    <p className="font-semibold text-blue-600">SAR 1200/night</p>
                  </CardContent>
                </Card>
                
                <Card className="overflow-hidden">
                  <div className="h-48 bg-blue-100 flex items-center justify-center">
                    <img 
                      src="https://placeholder-image-service.onrender.com/image/300x200?prompt=Contemporary hotel in urban setting with modern design&id=jd3" 
                      alt="Modern hotel building with sleek architecture in city center" 
                      className="w-full h-full object-cover"
                    />
                  </div>
                  <CardHeader>
                    <CardTitle className="text-lg">Radisson Blu Hotel</CardTitle>
                  </CardHeader>
                  <CardContent>
                    <p className="text-sm text-gray-600 mb-2">Modern hotel in the heart of Jeddah</p>
                    <p className="font-semibold text-blue-600">SAR 700/night</p>
                  </CardContent>
                </Card>
           
                <Card className="overflow-hidden">
                  <div className="h-48 bg-blue-100 flex items-center justify-center">
                    <img 
                      src="https://placeholder-image-service.onrender.com/image/300x200?prompt=Waterfront luxury hotel with elegant architecture&id=jd4" 
                      alt="Elegant hotel property located by the water with premium amenities" 
                      className="w-full h-full object-cover"
                    />
                  </div>
                  <CardHeader>
                    <CardTitle className="text-lg">InterContinental Jeddah</CardTitle>
                  </CardHeader>
                  <CardContent>
                    <p className="text-sm text-gray-600 mb-2">Elegant waterfront property with premium amenities</p>
                    <p className="font-semibold text-blue-600">SAR 950/night</p>
                  </CardContent>
                </Card>
                
                <Card className="overflow-hidden">
                  <div className="h-48 bg-blue-100 flex items-center justify-center">
                    <img 
                      src="https://placeholder-image-service.onrender.com/image/300x200?prompt=Luxury hotel with exceptional service and upscale design&id=jd5" 
                      alt="Premium hotel building with sophisticated architecture and landscaping" 
                      className="w-full h-full object-cover"
                    />
                  </div>
                  <CardHeader>
                    <CardTitle className="text-lg">Rosewood Jeddah</CardTitle>
                  </CardHeader>
                  <CardContent>
                    <p className="text-sm text-gray-600 mb-2">Luxury hotel with exceptional service and facilities</p>
                    <p className="font-semibold text-blue-600">SAR 1100/night</p>
                  </CardContent>
                  </Card>
              </>
            ) : null}

            {/* Makkah Hotels */}
            {activeTab === 'all' || activeTab === 'makkah' ? (
              <>
                <Card className="overflow-hidden">
                  <div className="h-48 bg-blue-100 flex items-center justify-center">
                    <img 
                      src="https://placeholder-image-service.onrender.com/image/300x200?prompt=Iconic hotel tower overlooking the Grand Mosque in Makkah&id=mk1" 
                      alt="Tall luxury hotel with view of the Grand Mosque in Makkah" 
                      className="w-full h-full object-cover"
                    />
                  </div>
                  <CardHeader>
                    <CardTitle className="text-lg">Makkah Clock Royal Tower</CardTitle>
                  </CardHeader>
                  <CardContent>
                    <p className="text-sm text-gray-600 mb-2">Iconic hotel overlooking the Grand Mosque</p>
                    <p className="font-semibold text-blue-600">SAR 1500/night</p>
                  </CardContent>
                </Card>
                
                
                <Card className="overflow-hidden">
                  <div className="h-48 bg-blue-100 flex items-center justify-center">
                    <img 
                      src="https://placeholder-image-service.onrender.com/image/300x200?prompt=Luxury hotel near Haram with elegant architecture&id=mk2" 
                      alt="Premium hotel building located close to the Holy Mosque" 
                      className="w-full h-full object-cover"
                    />
                  </div>
                  <CardHeader>
                    <CardTitle className="text-lg">Swissôtel Makkah</CardTitle>
                  </CardHeader>
                  <CardContent>
                    <p className="text-sm text-gray-600 mb-2">Luxury accommodations steps from Haram</p>
                    <p className="font-semibold text-blue-600">SAR 1300/night</p>
                  </CardContent>
                </Card>
                
                <Card className="overflow-hidden">
                  <div className="h-48 bg-blue-100 flex items-center justify-center">
                    <img 
                      src="https://placeholder-image-service.onrender.com/image/300x200?prompt=5-star hotel with breathtaking views of the Holy Mosque&id=mk3" 
                      alt="Luxury hotel offering panoramic views of the Grand Mosque" 
                      className="w-full h-full object-cover"
                    />
                  </div>
                  <CardHeader>
                    <CardTitle className="text-lg">Fairmont Makkah</CardTitle>
                  </CardHeader>
                  <CardContent>
                    <p className="text-sm text-gray-600 mb-2">5-star hotel with breathtaking mosque views</p>
                    <p className="font-semibold text-blue-600">SAR 1400/night</p>
                  </CardContent>
                </Card>
           
                <Card className="overflow-hidden">
                  <div className="h-48 bg-blue-100 flex items-center justify-center">
                    <img 
                      src="https://placeholder-image-service.onrender.com/image/300x200?prompt=Spacious hotel suites perfect for family accommodations&id=mk4" 
                      alt="Hotel with family-friendly suite accommodations and amenities" 
                      className="w-full h-full object-cover"
                    />
                  </div>
                  <CardHeader>
                    <CardTitle className="text-lg">Hilton Suites Makkah</CardTitle>
                  </CardHeader>
                  <CardContent>
                    <p className="text-sm text-gray-600 mb-2">Spacious suites perfect for families</p>
                    <p className="font-semibold text-blue-600">SAR 1200/night</p>
                  </CardContent>
                </Card>
                
                <Card className="overflow-hidden">
                  <div className="h-48 
bg-blue-100 flex items-center justify-center">
                    <img 
                      src="https://placeholder-image-service.onrender.com/image/300x200?prompt=Comfortable hotel with proximity to the Holy Mosque&id=mk5" 
                      alt="Hotel offering comfortable stays near the Grand Mosque" 
                      className="w-full h-full object-cover"
                    />
                  </div>
                  <CardHeader>
                    <CardTitle className="text-lg">Movenpick Hotel & Residences</CardTitle>
                  </CardHeader>
                  <CardContent>
                    <p className="text-sm text-gray-600 mb-2">Comfortable stay with Haram proximity</p>
                    <p className="font-semibold text-blue-600">SAR 1000/night</p>
                  </CardContent>
                </Card>
              </>
            ) : null}

            {/* Dubai Hotels (sample) */}
            {activeTab === 'all' || activeTab === 'dubai' ? (
              <>
                <Card className="overflow-hidden">
                  <div className="h-48 bg-blue-100 flex items-center justify-center">
                    <img 
                      src="https://placeholder-image-service.onrender.com/image/300x200?prompt=Iconic 7-star sail-shaped hotel in Dubai&id=db1" 
                      alt="Famous sail-shaped luxury hotel in Dubai with premium amenities" 
                      className="w-full h-full object-cover"
                    />
                  </div>
                  <CardHeader>
                    <CardTitle className="text-lg">Burj Al Arab Jumeirah</CardTitle>
                  </CardHeader>
                  <CardContent>
                    <p className="text-sm 
text-gray-600 mb-2">Iconic 7-star hotel with unmatched luxury</p>
                    <p className="font-semibold text-blue-600">$1500/night</p>
                  </CardContent>
                </Card>
                {/* Add 4 more Dubai hotels following the same pattern */}
            </>
            ) : null}

            {/* Worldwide Hotels (sample) */}
            {activeTab === 'all' || activeTab === 'worldwide' ? (
              <>
                <Card className="overflow-hidden">
                  <div className="h-48 bg-blue-100 flex items-center justify-center">
                    <img 
                      src="https://placeholder-image-service.onrender.com/image/300x200?prompt=Historic luxury hotel facing Central Park in New York&id=ww1" 
                      alt="Historic luxury hotel in New York with view of Central Park" 
                      className="w-full h-full object-cover"
                    />
                  </div>
                  <CardHeader>
                    <CardTitle className="text-lg">The Plaza Hotel, New York</CardTitle>
                  </CardHeader>
                  <CardContent>
                    <p className="text-sm text-gray-600 mb-2">Historic luxury hotel facing Central Park</p>
                    <p className="font-semibold text-blue-600">$1200/night</p>
                  </CardContent>
                </Card>
                {/* Add 4 more worldwide hotels following the same pattern */}
              </>
            ) : null}
          </div>
        </div>
      </section>

      {/* Contact Section */}
      <section id="contact" className="py-16 bg-blue-50">
        <div className="container mx-auto px-4">
          <div className="text-center mb-12">
            <h2 
className="text-3xl md:text-4xl font-bold text-blue-800 mb-4">Contact Us</h2>
            <p className="text-lg text-gray-600 max-w-3xl mx-auto">
              Get in touch with us to plan your next journey.
              We're here to assist you with all your travel needs.
            </p>
          </div>
          
          <div className="grid md:grid-cols-2 gap-12">
            <div>
              <h3 className="text-2xl font-semibold text-blue-700 mb-6">Our Information</h3>
              <div className="space-y-4">
                <div>
                  <h4 className="font-semibold text-blue-800">Phone Number</h4>
                  <p className="text-gray-700">+966 50 464 3552</p>
                </div>
                <div>
                  <h4 className="font-semibold text-blue-800">Email Address</h4>
                  <p className="text-gray-700">Alhamedmohd1234@yahoo.com</p>
                </div>
                <div>
                  <h4 className="font-semibold text-blue-800">Business Hours</h4>
                  <p className="text-gray-700">Monday - Sunday: 8:00 AM - 10:00 PM</p>
                </div>
                <div>
                  <h4 className="font-semibold text-blue-800">Licensing</h4>
                  <p className="text-gray-700">Fully licensed and accredited travel agency</p>
                </div>
              </div>
            </div>
            
            <div>
              <h3 className="text-2xl font-semibold text-blue-700 mb-6">Send us a Message</h3>
              {isSubmitted ?
              (
                <div className="bg-green-100 border border-green-400 text-green-700 px-4 py-3 rounded">
                  Thank you for your message! We'll get back to you soon.
                </div>
              ) : (
                <form 
                  onSubmit={handleSubmit} className="space-y-4">
                  <div>
                    <label htmlFor="name" className="block text-blue-800">Your Name</label>
                    <input 
                      id="name" 
                      type="text" 
                      value={name}
                      onChange={(e) => setName(e.target.value)}
                      required 
                      className="mt-1 w-full p-2 border border-gray-300 rounded"
                    />
                  </div>
                  <div>
                    <label htmlFor="email" className="block text-blue-800">Email Address</label>
                    <input 
                      id="email" 
                      type="email" 
                      value={email}
                      onChange={(e) => setEmail(e.target.value)}
                      required 
                      className="mt-1 w-full p-2 border border-gray-300 rounded"
                    />
                  </div>
                  <div>
                    <label htmlFor="message" className="block text-blue-800">Your Message</label>
                    <textarea 
                      id="message" 
                      value={message}
                      onChange={(e) => setMessage(e.target.value)}
                      required 
                      className="mt-1 w-full p-2 border border-gray-300 rounded h-32"
                    />
                  </div>
                  <button type="submit" className="w-full bg-blue-600 hover:bg-blue-700 text-white p-3 rounded-lg">Send Message</button>
                </form>
              )}
            </div>
          </div>
        </div>
      </section>

      {/* Footer */}
      <footer className="bg-blue-900 text-white py-8">
        <div className="container mx-auto px-4">
          <div className="flex flex-col md:flex-row justify-between items-center">
            <div className="mb-4 md:mb-0">
              <h3 className="text-2xl font-bold">Alhamed Tours & Travels</h3>
              <p className="text-blue-200">Your trusted travel partner since 2010</p>
              {/* UPDATED: Added domain name */}
              <p className="text-blue-200 mt-1">Visit us at **Alhamedtoursandtravel.com**</p>
            </div>
            <div 
              className="text-center md:text-right">
              <p className="text-blue-200">© {new Date().getFullYear()} Alhamed Tours & Travels.
              All rights reserved.</p>
              <p className="text-blue-200">Licensed and accredited by Saudi Tourism Authority</p>
            </div>
          </div>
        </div>
      </footer>
    </div>
  );
};

export default AlhamedToursTravels;
