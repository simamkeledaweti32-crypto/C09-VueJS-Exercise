<template>
  <div>
    <h1>Cape Town Food Fest 2025</h1>
    <div class="tickets-grid">
      <div class="ticket-card" v-for="ticket in tickets" :key="ticket.id">
        <h2 class="ticket-title">{{ ticket.title }}</h2>
        <div class="ticket-price">R{{ ticket.price }}</div>
        
        <span :class="['difficulty', ticket.difficulty]">{{ ticket.difficulty.toUpperCase() }}</span>
        
        <ul class="benefits">
          <li v-for="benefit in ticket.benefits" :key="benefit">{{ benefit }}</li>
        </ul>
        
        <p :class="['tickets-left', { low: ticket.ticketsLeft < 20 }]">
          Tickets left: {{ ticket.ticketsLeft }}
        </p>
        
        <button 
          v-if="ticket.ticketsLeft > 0" 
          class="reserve-btn" 
          @click="reserveTicket(ticket)"
        >
          Reserve Now
        </button>
        <div v-else class="sold-out">SOLD OUT</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tickets: [
        {
          id: 1,
          title: "Standard Day Pass",
          price: 250,
          difficulty: "standard",
          ticketsLeft: 150,
          benefits: ["Access to all food stalls", "Live cooking demos", "Free recipe booklet"]
        },
        {
          id: 2,
          title: "VIP Experience",
          price: 550,
          difficulty: "vip",
          ticketsLeft: 45,
          benefits: ["Everything in Standard", "Chef meet & greet", "VIP seating area", "Welcome drink"]
        },
        {
          id: 3,
          title: "Premium Weekend Pass",
          price: 950,
          difficulty: "premium",
          ticketsLeft: 12,
          benefits: ["2-Day access", "All VIP benefits", "Cooking masterclass", "Exclusive merchandise"]
        }
      ]
    }
  },
  methods: {
    reserveTicket(ticket) {
      if (ticket.ticketsLeft > 0) {
        ticket.ticketsLeft--;
        alert(`Reserved 1 ${ticket.title} ticket! ${ticket.ticketsLeft} left.`);
      }
    }
  }
}
</script>
