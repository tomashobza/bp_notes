![[Pasted image 20241013203132.png]]
![[Pasted image 20241013203137.png]]

Je zřejmé, že jedenáct snímků je příliš malý počet pro úspěšnou rekonstrukci. Algoritmus ovšem úspěšně detekoval charakteristické body. Z experimentu také plyne nutnost překrývajících se snímků \- zachycení kontinuálního videa bude proto nejlepším možným řešením. 

Pro optimalizaci lze násobit rychlost pořizování snímků rychlostí pohybu drona. Při nižších rychlostech se obsah snímané scény mění pomaleji, proto není třeba rapidního snímání.

Následně jsem vyzkoušel tři hlavní algoritmy pro extrakci charakteristických bodů a jejich následné párování \- SIFT, FAST a ORB. Nejprve jsem vyzkoušel extrakci samotnou.

![[Pasted image 20241013203156.png]]

A následně jsem vyzkoušel extrakci a párování charakteristických bodů. Obrázky jsou

![[Pasted image 20241013203207.png]]
![[Pasted image 20241013203223.png]]
![[Pasted image 20241013203227.png]]
Zde vizualizováno znovu se snímky z videa z dronu:
![[Pasted image 20241013212336.png]]
![[Pasted image 20241013212338.png]]
![[Pasted image 20241013212341.png]]
