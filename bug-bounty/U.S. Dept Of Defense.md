# Cors Missconfig no departamento de defesa dos eua (Department of Defense Cyber Crime Center: DC3)
# Entry points
encontrei 2 possíveis entry points em um dos maiores sites do dept de defesa dos eua,
e um válido, o site era do centro de crimes cibernéticos -> encontrei ele em um programa
de bug bounty na HackerOne
# SSL mal configurado
verifiquei o site e achei o primeiro possível entry point
no certificado SSL do site, onde o certificado SSL não correspondia ao CN (common name)
do www.defense.gov essa vulnerabilidade pode permitir atacantes usarem técnicas
de spoofing (se passar por algo como fingir ser o site)
depois de tentar validar o entry point desisti dela porquê os requerimentos
do escopo do programa de bug bounty do dept de defesa era muito rigoroso
e não permitia nada relacionado a exploração de vulnerabilidades encontradas
