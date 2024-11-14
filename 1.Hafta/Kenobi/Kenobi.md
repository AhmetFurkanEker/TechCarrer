[[Kenobi/Ağ Tarama/Nmap]] taramasında görüldüğü üzere Samba aracılığıyla paylaşılan dizinleri ve zafiyetli(Path Variable Manipulation) olan proftp yazılımı aracılığıyla sistem içersinde bir takım işlemler yapacağız. 

> - **SMB:** Dosya ve yazıcı paylaşımı için kullanılan bir ağ protokolüdür.
> - **Samba:** Linux ve Unix sistemlerinde SMB protokolünü uygulayan açık kaynaklı bir yazılımdır, Windows ile dosya ve yazıcı paylaşımı yapmayı sağlar.


>Enumeratıon , sızma testlerinde farklı protokolleri hedef alarak bu protokoller aracılığıyla sistem hakkında bilgiler toplanılan ve bu bilgilerle bir atak haritası oluşturulan kısımdır. 


`139/tcp  open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP) ,445/tcp  open  netbios-ssn Samba smbd 4.3.11-Ubuntu (workgroup: WORKGROUP)`  nmap taramamız bize böyle bir çıktı vermişti. Sambayı kullanarak sistem üzerinde paylaşılan dizinler,makine bilgileri vey çeşitrli zafiyetler keşfederek sisteme sızma testimizi yol haritası çıkartacağız. 


