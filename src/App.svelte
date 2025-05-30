<script>
  import FeedbackList from "./components/FeedbackList.svelte";

let feedback = [

{
  id: 1,
  rating: 10,
  text: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Officia voluptas veniam eum ad. Praesentium, itaque? Aliquam perferendis asperiores vitae laborum, esse deserunt, illum ipsam animi molestias id dicta sapiente aperiam.',
},

{
  id: 2,
  rating: 9,
  text: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Officia voluptas veniam eum ad. Praesentium, itaque? Aliquam perferendis asperiores vitae laborum, esse deserunt, illum ipsam animi molestias id dicta sapiente aperiam.',
},

{
  id: 3,
  rating: 8,
  text: 'Lorem ipsum dolor, sit amet consectetur adipisicing elit. Officia voluptas veniam eum ad. Praesentium, itaque? Aliquam perferendis asperiores vitae laborum, esse deserunt, illum ipsam animi molestias id dicta sapiente aperiam.',
}


]

//Action Delete
const deleteFeedback = (e) =>{
   const itemId = e.detail
   feedback = feedback.filter((item)=> item.id != itemId)
}
</script>

<main class="container">
   <FeedbackList {feedback} on:delete-feedback ={deleteFeedback} />

</main>

