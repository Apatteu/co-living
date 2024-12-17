<script>
  import { Card, Button } from 'flowbite-svelte';
  import { ArrowRightOutline } from 'flowbite-svelte-icons';
  import { SearchOutline } from 'flowbite-svelte-icons';

  // Apartment card data
  const apartments = [
    {
      title: 'Noteworthy technology acquisitions 2021',
      description: 'Here are the biggest enterprise technology acquisitions of 2021 so far.',
      price: '₱8,000 – ₱15,000',
      img: '/image/B1.jpg',
      rating: 4
    },
    {
      title: 'Luxury Apartment in the City Center',
      description: 'A beautiful apartment located in the heart of the city with modern amenities.',
      price: '₱20,000 – ₱25,000',
      img: '/image/B2.jpg',
      rating: 5
    },
    {
      title: 'Cozy Studio with Scenic Views',
      description: 'A cozy and compact studio apartment with breathtaking views of the skyline.',
      price: '₱10,000 – ₱12,000',
      img: '/image/building.jpg',
      rating: 3
    },
    {
      title: 'Spacious 2-Bedroom Apartment',
      description: 'Spacious and well-lit 2-bedroom apartment perfect for a small family.',
      price: '₱15,000 – ₱18,000',
      img: '/image/building.jpg',
      rating: 4
    },
    {
      title: 'Modern Loft with Private Balcony',
      description: 'A sleek modern loft with a private balcony overlooking the park.',
      price: '₱18,000 – ₱22,000',
      img: '/image/building.jpg',
      rating: 5
    },
    {
      title: 'Quiet Apartment with Large Garden',
      description: 'A peaceful apartment with a large garden, perfect for nature lovers.',
      price: '₱12,000 – ₱16,000',
      img: '/image/building.jpg',
      rating: 2
    }
  ];
</script>

<style>
  .search-bar {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 0rem;
    margin: 1rem 0;
    position: relative;
  }

  .cards-container {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
    gap: 1.5rem;
    padding: 2rem;
  }
</style>

<!-- Search Bar -->
<div class="search-bar flex items-center">
  <div class="relative">
    <select class="form-select px-4 py-2 border rounded">
      <option selected>All categories</option>
      <option>Room Type</option>
      <option>Preferred Roommates</option>
      <option>House Rules</option>
    </select>
  </div>
  <input
    type="text"
    placeholder="Search Units..."
    class="form-input px-4 py-2 border rounded w-1/2"
  />
  <button class="px-4 py-2 rounded bg-blue-600 text-white hover:bg-blue-700 focus:ring-4 focus:ring-blue-300 flex justify-center items-center">
    <SearchOutline class="w-5 h-5" />
  </button>
</div>

<!-- Apartment Cards -->
<div class="cards-container">
  {#each apartments as apartment}
    <Card img={apartment.img}>
      <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
        {apartment.title}
      </h5>
      <p class="mb-3 font-normal text-gray-700 dark:text-gray-400 leading-tight">
        {apartment.description}
      </p>

      <!-- Star Rating -->
      <div class="flex items-center mb-2">
        {#each Array(5).fill(0) as _, i}
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill={i < apartment.rating ? "gold" : "none"}
            viewBox="0 0 24 24"
            stroke="gold"
            class="w-5 h-5"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M12 17.27L18.18 21l-1.64-7.03L22 9.24l-7.19-.61L12 2 9.19 8.63 2 9.24l5.46 4.73L5.82 21z"
            />
          </svg>
        {/each}
      </div>

      <div class="flex items-center space-x-4">
        <p class="text-sm font-semibold text-green-700">{apartment.price}</p>
        <Button style="background-color: blue; color: white;">
          Read more
          <ArrowRightOutline class="w-6 h-6 ms-2 text-white" />
        </Button>
      </div>
    </Card>
  {/each}
</div>
