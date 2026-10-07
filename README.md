# Egyeb
Segédlet
"""
CSS..
.class_elem{
width: 500px;
padding-top: 1em;
height: 200px;
}
.class_elem > h3{
    font-family: "Dancing Script", cursive;
    font-optical-sizing: auto;
    font-weight:bold;
    font-style:normal;
      font-size: 1.5em;
      text-align: center;
}
.class_elem > img{
    width:50%;
    padding: 1em;
    border-radius: 1.5em;
   
}
.class_elem:nth-of-type(even) > img{
    float:left;
}
.class_elem:nth-of-type(odd) > img{
    float:right;
}
CSS 2...
#velemid{
    display: flex;
	flex-direction: row;
	flex-wrap: wrap;
	justify-content: center;
	align-items: center;
	align-content: stretch;
    gap: 2em;
}
#velemid > h3{
    width: 100%;
    font-family: "Dancing Script", cursive;
    font-optical-sizing: auto;
    font-weight:bold;
    font-style:normal;
      font-size: 2.0em;
      text-align: center;
}
"""
Segédlet:
    internal class Feladat
    {
        List<Konyv> adatok = [];

        public Feladat()
        {
            foreach (var item in File.ReadAllLines("konyv.csv",Encoding.UTF8).Skip(1))
            {
                string[] resz=item.Split(';');
                string cim=resz[0];
                string nev=resz[1];
                string nemzetiseg=resz[2];
                int szulEv=int.Parse(resz[3]);
                int halEv=Convert.ToInt32(resz[4]);
                int helyezes=int.Parse(resz[5]);
                adatok.Add(new(cim,nev,nemzetiseg,szulEv,halEv,helyezes));
            }
        }
        public void Feladat4()
        {
            Console.WriteLine($"4. Feladat: A könyvek száma: {adatok.Count} db");
        }

        public void Feladat5()
        {
            Console.WriteLine("5. Feladat: A még élő szerzők művei: ");

            var eredmeny = adatok.Where(x => x.halEv == 0);
            foreach (var item in eredmeny)
            {
                Console.WriteLine(item.Cim);
            }


        }
        public void Feladat7()
        {
            Console.Write("7. feladat: Kérem a szerző nemzetiségét: ");
            var bekertNemzet = Console.ReadLine();
            var eredmeny = adatok.Where(x => x.Nemzetiseg == bekertNemzet);
            if (eredmeny.Count() == 0) 
            {
                Console.WriteLine("Nem található szerző a megadott nemzetiségből.");
            }
            else
            {
                double atlag = eredmeny.Average(x => x.helyezes);
                Console.WriteLine($"A szerzők műveinek átlagos helyezése: {atlag:N1}");
            }

        }
---------------------------map
		function UserList() {
  const users = [
    { id: 'u1', name: 'Anna' },
    { id: 'u2', name: 'Péter' },
    { id: 'u3', name: 'Kata' }
  ];

  return (
    <ul>
      {users.map(user => (
        <li key={user.id}>{user.name}</li>
      ))}
    </ul>
  );
}
------------------komp
import { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div style={{ padding: '20px', fontFamily: 'sans-serif' }}>
      <h2>Számláló Komponens</h2>
      <p>A gombot eddig <strong>{count}</strong> alkalommal nyomtad meg.</p>
      <button onClick={() => setCount(count + 1)}>
        Kattints ide!
      </button>
    </div>
  );
}

export default Counter;
-----------------------------------
