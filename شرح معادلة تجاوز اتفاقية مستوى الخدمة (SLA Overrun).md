#  شرح معادلة تجاوز اتفاقية مستوى الخدمة (SLA Overrun)

## 1. المقدمة (Introduction)

تهدف هذه المذكرة إلى توضيح وشرح معادلة احتساب نسبة تجاوز اتفاقية مستوى الخدمة (SLA Overrun) بطريقة مبسطة وواضحة، لضمان فهم دقيق وتطبيق فعال في التقارير الإدارية، خاصة عند التعامل مع حالات متعددة ضمن نفس حالة العمل (Workflow State).

This memo aims to clarify and explain the Service Level Agreement (SLA) Overrun calculation formula in a simple and clear manner, ensuring accurate understanding and effective application in management reports, especially when dealing with multiple cases within the same Workflow State.

## 2. الهدف الأساسي (Core Objective)

الهدف الأساسي هو قياس نسبة التأخير فوق الحد المسموح به لكل حالة عمل (Workflow State) بطريقة عادلة. فبما أن وقت الـ SLA محدد لكل استقالة على حدة، وليس للمجموعة ككل، يجب تعديل طريقة الحساب لتعكس هذا الواقع.

The core objective is to fairly measure the percentage of delay beyond the allowed limit for each Workflow State. Since the SLA time is defined for each individual resignation, and not for the group as a whole, the calculation method must be adjusted to reflect this reality.

## 3. الفكرة الأساسية (Basic Concept)

عندما يعرض لوحة التحكم (Dashboard) بطاقة واحدة تحتوي على أكثر من استقالة داخل نفس حالة العمل (مثلاً: 32 استقالة)، فإنه من غير الصحيح مقارنة مجموع أيام الانتظار لهذه الاستقالات مع SLA استقالة واحدة. هذا النهج يؤدي إلى نسب مبالغ فيها وغير عادلة.

الحل الصحيح هو تحويل إجمالي وقت الـ SLA المسموح به للمجموعة كلها، وذلك بضرب وقت الـ SLA المخصص لاستقالة واحدة بعدد الاستقالات الموجودة ضمن نفس الحالة.

When the Dashboard displays a single card containing more than one resignation within the same Workflow State (e.g., 32 resignations), it is incorrect to compare the total pending days for these resignations with the SLA of a single resignation. This approach leads to exaggerated and unfair percentages.

The correct solution is to convert the total allowed SLA time for the entire group by multiplying the SLA time allocated for a single resignation by the number of resignations within the same state.

## 4. المعادلة المقترحة (Proposed Formula)

**إجمالي الأيام المسموح بها لاتفاقية مستوى الخدمة (Total SLA Allowed Days):**

`Total SLA Allowed Days = SLA Days x Number of Resignations`

**نسبة التجاوز (Overrun %):**

`Overrun % = ((Total Pending Days - Total SLA Allowed Days) / Total SLA Allowed Days) x 100`

## 5. تعريف المصطلحات (Definitions)

| المصطلح (Term)           | المعنى (Meaning)                                                                 |
| :---------------------- | :------------------------------------------------------------------------------- |
| Number of Resignations  | عدد الاستقالات الموجودة في نفس حالة العمل (Workflow State).                      |
| SLA Days                | عدد الأيام المسموح بها لاستقالة واحدة داخل هذه الحالة.                           |
| Total Pending Days      | مجموع الأيام الفعلية التي انتظرتها كل الاستقالات داخل نفس الحالة.                |
| Total SLA Allowed Days  | إجمالي الأيام المسموحة لكل الاستقالات داخل نفس الحالة.                           |
| % Overrun               | نسبة التجاوز فوق الوقت المسموح. إذا كانت صفر بالمئة أو أقل فهذا يعني أن المجموعة ضمن SLA. |

## 6. مثال مبسط من لوحة التحكم (Simplified Dashboard Example)

لنفترض أن لوحة التحكم تعرض البيانات التالية:

| العنصر (Item)                     | القيمة (Value)                                  |
| :-------------------------------- | :--------------------------------------------- |
| Workflow State                    | Pending By HR Administration Section           |
| Number of Resignations            | 32                                             |
| Average Pending Days              | 70.34 يوم (days)                               |
| SLA Days                          | 15 يوم لكل استقالة داخل هذه الحالة (مثال توضيحي) |

**أولاً: نحسب مجموع الأيام الفعلية التي انتظرتها كل الاستقالات (Total Pending Days):**

`Total Pending Days = Average Pending Days x Number of Resignations`
`Total Pending Days = 70.34 x 32 = 2,250.88 days`

**ثانياً: نحسب إجمالي الأيام المسموحة للمجموعة (Total SLA Allowed Days):**

`Total SLA Allowed Days = SLA Days x Number of Resignations`
`Total SLA Allowed Days = 15 x 32 = 480 days`

**ثالثاً: نحسب نسبة التجاوز (Overrun %):**

`Overrun % = ((2,250.88 - 480) / 480) x 100`
`Overrun % = 368.93% ≈ 369%`

**تفسير النتيجة (Result Interpretation):**

المجموعة تجاوزت الـ SLA بنسبة تقريبية 369% فوق الحد المسموح. بمعنى آخر، الوقت المسموح للمجموعة هو 480 يوم، لكن الوقت الفعلي وصل إلى 2,250.88 يوم؛ أي يوجد تجاوز مقداره 1,770.88 يوم فوق المسموح.

The group exceeded the SLA by approximately 369% above the allowed limit. In other words, the allowed time for the group is 480 days, but the actual time reached 2,250.88 days; meaning there is an overrun of 1,770.88 days above the allowed limit.
