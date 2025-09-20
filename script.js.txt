document.getElementById("storyForm").addEventListener("submit", function(e) {
  e.preventDefault();

  const name = document.getElementById("name").value;
  const theme = document.getElementById("theme").value;
  const length = document.getElementById("length").value;
  let price = parseInt(document.getElementById("price").value);

  if (price < 4000) price = 4000;
  if (price > 60000) price = 60000;

  // --- Simulation d’histoire ---
  const story = `
Il était une fois ${name}, un héros/une héroïne courageux(se).
Son aventure commença dans un monde rempli de ${theme}.
Cette histoire est de longueur ${length}.
(✨ Ceci est un exemple. Bientôt l’IA générera une vraie histoire personnalisée ✨)
  `;

  document.getElementById("storyOutput").textContent = story;
  document.getElementById("storyResult").classList.remove("hidden");

  // --- Préparer le PDF ---
  const blob = new Blob([story], { type: "application/pdf" });
  const url = URL.createObjectURL(blob);
  document.getElementById("downloadLink").href = url;

  alert(`Merci ! Veuillez effectuer un paiement de ${price.toLocaleString()} FCFA au numéro 074010303 (Airtel Money)`);
});
