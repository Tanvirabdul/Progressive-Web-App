<template>
 <section class="p-5  d-flex">
    <aside>
      <h6>Sort By:</h6>
      <div>
        <input type="radio" name="sortby" v-on:change="sortBy($event)" 
        value="Subject">Subject</div>
      <div>
        <input type="radio" name="sortby" v-on:change="sortBy($event)" 
        value="Location">Location</div>
      <div>
        <input type="radio" name="sortby" v-on:change="sortBy($event)" 
        value="Price">Price</div>
      <div>
        <input type="radio" name="sortby" v-on:change="sortBy($event)" 
        value="Availability">Availability</div>
      <br>
      <h6>Order in:</h6>
      <div><input type="radio" name="orderin" v-on:change="sortBy($event)"
         value="Asc">Ascending</div>
      <div><input type="radio" name="orderin" v-on:change="sortBy($event)" 
        value="Desc">Descending</div>
      
    </aside>
    <div class="container px-4 px-lg-5 mt-2">
        <div class="row gx-4 gx-lg-5 row-cols-2 row-cols-md-3 row-cols-xl-4 mb-5">
            <input type="search" class="form-control" @keydown="searchLessons" placeholder="Search lessons...">
        </div>
        <div class="row gx-4 gx-lg-5 row-cols-2 row-cols-md-3 row-cols-xl-4">
            <div class="col mb-5 product" :key="product.id"  v-for="product in products">
                <div class="card h-100">
                    <div class="card-body p-4">
                        <div class="text-center">
                            <h5 class="fw-bolder">Subject: {{product.Subject}}</h5>
                            <p>Location: {{product.Location}}</p>
                            <p>Spaces: {{product.Space }}</p>
                            Price: £{{product.Price}}
                        </div>
                    </div>
                    <div class="card-footer p-4 pt-0 border-top-0 bg-transparent">
                        <div class="text-center" v-if="product.Space > 0"><a class="btn btn-outline-dark mt-auto" v-on:click="addToCart(product.id)" >Add to Cart</a></div>
                        <div class="text-center disabled" v-else><a class="btn btn-outline-dark mt-auto" >Add to Cart</a></div>
                    </div>
                </div>
            </div>
        </div>
        <div v-show="cart.length > 0">
            <h1 class="text-center" >Shopping Cart</h1>
                <div class="row gx-4 gx-lg-5 row-cols-2 row-cols-md-3 row-cols-xl-4 justify-content-center">
                <div class="col mb-5 product" :key="product.id"  v-for="product in cart">
                    <div class="card h-100">
                        <div class="card-body p-4">
                            <div class="text-center">
                                <h5 class="fw-bolder">Subject: {{product.Subject}}</h5>
                                <p>Location: {{product.Location}}</p>
                                <p>Spaces: {{product.Space }}</p>
                                Price: £{{product.Price}}
                            </div>
                        </div>
                        <div class="card-footer p-4 pt-0 border-top-0 bg-transparent">
                            <div class="text-center disabled"><a class="btn btn-outline-danger mt-auto" v-on:click="removeFromCart(product.id)">Remove</a></div>
                        </div>
                    </div>
                </div>
                </div>
        </div>
        <div>
            <h1 class="text-center">Checkout</h1>
            <form class="d-flex justify-content-between" v-on:submit="handleSubmit">
                <div>
                <label>Name:</label>
                <input type="text" name="name" class="border-top-0 border-start-0 border-end-0">
                </div>
                <div>
                <label>Phone:</label>
                <input type="text" name="phone" class="border-top-0 border-start-0 border-end-0">
                </div>
                <div><button class="btn btn-outline-dark mt-auto">Checkout</button></div>
            </form>
        </div>
    </div>
</section>
</template>

<script>
export default {
  name: 'WelcomeComponent',
  props: {
  },
};
</script>
