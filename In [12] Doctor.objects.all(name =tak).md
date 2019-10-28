n [1]:  d1 = Doctor.objects.get(id=1)

In [2]: p1 = Patient.objects.get(id=1)

In [3]: r1 = Reservation.objects.create(doctor=d1,patient=p1)

In [4]: r1
Out[4]: <Reservation: John 의사: change 환자>

In [5]: doctor1 = Doctor.objects.create(name="tak")
   ...: doctor2 = Doctor.objects.create(name="zzulu")
   ...: doctor3 = Doctor.objects.create(name="neo")
   ...: 
   ...: patient1 = Patient.objects.create(name="junho")
   ...: patient2 = Patient.objects.create(name="jason")
   ...: patient3 = Patient.objects.create(name="justin")
  File "<ipython-input-5-e19b92e7d401>", line 4
    
    ^
SyntaxError: invalid character in identifier


In [6]:  doctor1 = Doctor.objects.create(name="tak")

In [7]: doctor2 = Doctor.objects.create(name="zzulu")

In [8]: doctor3 = Doctor.objects.create(name="neo")

In [9]: patient1 = Patient.objects.create(name="junho")
   ...: patient2 = Patient.objects.create(name="jason")
   ...: patient3 = Patient.objects.create(name="justin")

In [10]: reservation1 = Reservation.objects.create(doctor=doctor1, patient=patient1)
    ...: reservation2 = Reservation.objects.create(doctor=doctor1, patient=patient2)
    ...: reservation3 = Reservation.objects.create(doctor=doctor2, patient=patient3)
    ...: reservation4 = Reservation.objects.create(doctor=doctor2, patient=patient1)
    ...: reservation5 = Reservation.objects.create(doctor=doctor3, patient=patient3)

In [11]: doctor1
Out[11]: <Doctor: tak>

In [12]: Doctor.objects.all(name ="tak")
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-12-3e15422f062a> in <module>
----> 1 Doctor.objects.all(name ="tak")

TypeError: all() got an unexpected keyword argument 'name'

In [13]: Docotr
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-13-973262188519> in <module>
----> 1 Docotr

NameError: name 'Docotr' is not defined

In [14]: Doctor
Out[14]: manytomany.models.Doctor

In [15]: Doctor.name
Out[15]: <django.db.models.query_utils.DeferredAttribute at 0x172e717e188>

In [16]: Doctor.filter(name="tak")
---------------------------------------------------------------------------
AttributeError                            Traceback (most recent call last)
<ipython-input-16-ee40ce2f60c7> in <module>
----> 1 Doctor.filter(name="tak")

AttributeError: type object 'Doctor' has no attribute 'filter'

In [17]: doctor1.reservation_set.all()
Out[17]: <QuerySet [<Reservation: tak 의사: junho 환자>, <Reservation: tak 의사: jason 환자>]>

In [18]: for reservation in doctor1.reservation_set.all():
    ...:     print(resevation.patient.name)
    ...: 
---------------------------------------------------------------------------
NameError                                 Traceback (most recent call last)
<ipython-input-18-c84293a33371> in <module>
      1 for reservation in doctor1.reservation_set.all():
----> 2     print(resevation.patient.name)
      3

NameError: name 'resevation' is not defined

In [19]: for reservation in doctor1.reservation_set.all():
    ...:     print(reservation.patient.name)
    ...: 
    ...: 
junho
jason

In [20]: for reservation in patient1.reservation_set.all():
    ...:     print(reservation.doctor.name)
    ...: 
tak
zzulu







In [3]: doctor1.patients.all()
Out[3]: <QuerySet [<Patient: junho>, <Patient: jason>]>

In [4]: patient1.doctors.all()
Out[4]: <QuerySet [<Doctor: tak>, <Doctor: zzulu>]>