| **Tesztelt követelmény**                                           | **Előfeltételek (kiindulási állapot)**                      | **A teszt lépései**                    | **Elvárt kimenet/eredmény**                            |
|--------------------------------------------------------------------|-------------------------------------------------------------|----------------------------------------|--------------------------------------------------------|
| Csak az egyik (SINGLE) torpedó tárat tüzelje, ha van torpedó       | Mindkét tárban van torpedó                                  | `fireTorpedo(SINGLE)`                  | SUCCESS                                                |
| A következő lövésnél a másik tárat tüzelje (alternálás)            | Mindkét tárban van torpedó, az első lövés után az egyik üres | `fireTorpedo(SINGLE)` kétszer          | SUCCESS mindkét alkalommal                             |
| Ha az aktuális (sorrendi) tár üres, a másik tárat tüzelje          | Csak az egyik tárban van torpedó, első lövésnél az üres     | `fireTorpedo(SINGLE)`                  | SUCCESS                                                |
| Ha az aktuális (sorrendi) tár sikertelenül tüzel, a másikat ne tüzelje | Mindkét tárban van torpedó, az egyik lövés sikertelen      | `fireTorpedo(SINGLE)`                  | FAIL (nem próbálja meg újra a másik tárat tüzelni)  |
| Mindkét tár tüzel, ha ALL módban van és van torpedó mindkét tárban | Mindkét tárban van torpedó                                  | `fireTorpedo(ALL)`                     | SUCCESS                                                |
| ALL mód sikeres, ha az egyik tár tüzel        | Az egyik tárban van torpedó, a másik tár hibás              | `fireTorpedo(ALL)`                     | SUCCESS (egy tár tüzel)                        |
| ALL mód sikertelen, ha egyik tár sem tüzel        | Az egyik tárban nincs torpedó, a másik tár hibás              | `fireTorpedo(ALL)`                     | FAIL (egy tár sem tüzel)                        |
| Ha nincs torpedó egyik tárban sem, a lövés nem sikerül             | Mindkét tár üres                                            | `fireTorpedo(SINGLE)` vagy `fireTorpedo(ALL)` | FAIL                                          |