let palavra;

function setup() {
  createCanvas(600, 400);
  palavra = palavraAleatoria();
}

function palavraAleatoria() {
  let palavras = ["Caminhante", "Caminho", "Caminha", "Destino", "Viagem", "Percurso"];
  return random(palavras);
}

function inicializaCores() {
  background(random(200, 255)); // Fundo com tons aleatórios claros
  fill(random(50, 100), 50, random(150, 200)); // Texto com variação de azul/roxo
  textSize(64);
  textAlign(CENTER, CENTER);
}

function palavraParcial(minimo, maximo) {
  let quantidade = map(mouseX, minimo, maximo, 1, palavra.length);
  let parcial = palavra.substring(0, quantidade);
  return parcial;
}

function draw() {
  inicializaCores();

  let parcial = palavraParcial(0, width);

  // Exibe a palavra parcial no centro
  text(parcial, width / 2, height / 2);

  // Exibe instruções na parte inferior
  fill(50);
  textSize(20);
  text("Mova o mouse para revelar a palavra. Pressione ESPAÇO para trocar.", width / 2, height - 30);
}

function keyPressed() {
  if (key === ' ') { // Troca a palavra ao pressionar espaço
    palavra = palavraAleatoria();
  }
}
