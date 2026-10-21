# Password Policy – LabSec Solutions

1. Minimální délka hesla: 12 znaků  
2. Kombinace velkých a malých písmen, číslic a speciálních znaků  
3. Hesla se mění při podezření na kompromitaci (v souladu s NIST SP 800-63B se nevyžaduje pravidelná periodická změna)  
4. Nesmí se opakovat posledních 5 hesel  
5. Admin účty: min. 16 znaků, povinné 2FA  
6. Zakázáno používat osobní údaje nebo jednoduchá hesla typu 12345  
7. Hesla se ukládají hashovaná (/etc/shadow)  
8. Přístup je blokován po 5 neúspěšných pokusech  
9. Defaultní hesla jsou zakázána a musí být změněna při prvním použití  
10. Doporučeno používat password manager (Bitwarden, KeePassXC)
