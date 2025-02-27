1. Что такое Kubernetes?
<details>
  <summary>Ответ</summary>
Kubernetes (также известный как K8s или «kube») – система, управляющая контейнерами* (контейнеризированными приложениями), где контейнер объясняется как «легковесная» виртуальная машина. Чтобы создать приложение, необходимо создать множество контейнеров, а затем использовать Kubernetes для управления этими контейнерами.
</details>

2. Расскажите об основных компонентах kubernetes?
<details>
  <summary>Ответ</summary>
На мастер-узле, также известном как Control Plane (иногда его переводят как «управляющий слой» — прим. перев.), выполняется большинство важных задач по управлению и администрированию кластера. 

Он включает в себя четыре основных компонента:

- API server (API-сервер);
  
- scheduler (планировщик);
  
- controller manager (менеджер контроллеров);

- etcd.
 
Мы уже рассмотрели, что такое мастер-узел. Но настоящая работа происходит именно на рабочих узлах. А всё потому, что на каждом узле есть компоненты, отвечающие за его бесперебойное функционирование

Они включают в себя:

kubelet;
  
kube-proxy;
  
container runtime.
</details>

3. Что такое API server (API-сервер) master node ? 
<details>
  <summary>Ответ</summary>
Для любых манипуляций с кластером приходится обращаться к API-серверу с помощью Kubernetes API. Используете kubectl, REST или любую из клиентских библиотек Kubernetes? Все они завязаны на API Kubernetes'а и взаимодействуют с API-сервером.

Примечательная особенность API-сервера состоит в том, что он умеет масштабироваться по горизонтали. Другими словами, при резком увеличении количества поступающих запросов API-сервер может создавать «клоны» или реплики самого себя, чтобы справиться с нагрузкой.
</details>

4. Что такое scheduler (планировщик) master node ?
<details>
  <summary>Ответ</summary>
Каждому Pod’у требуются определенные ресурсы: память, CPU, железо… в общем, стандартный набор. Планировщик должен решить, какой узел соответствует требованиям Pod’а. Поэтому планировщик выполняет два действия:

Подбирает узлы-кандидаты для Pod’а;

Останавливает свой выбор на одном из них.
</details>

5. Что такое controller-manager?
<details>
  <summary>Ответ</summary>
На самом деле контроллер — это просто бесконечный цикл, который постоянно следит за неким ресурсом в кластере (например, за Pod’ом). Если что-то идет не так, он исправляет возникшую проблему.
</details>

6. Какие типы controller-manager вы знаете?
<details>
  <summary>Ответ</summary>
endpoints controller - заполняет объект конечных точек (Endpoints), то есть связывает сервисы (Services) и поды (Pods)

service accounts controller и token controller -  создают стандартные учетные записи и токены доступа API для новых пространств имен.

replication controller - поддерживает правильное количество подов для каждого объекта контроллера репликации в системе

</details>

7. Для чего etcd в kubernetes?
<details>
  <summary>Ответ</summary>
Etcd — это личный журнал Kubernetes. Скажите, зачем люди ведут личные дневники и журналы? Все просто: чтобы сохранить в памяти мимолетные моменты (увы, мозг не способен хранить все события каждого дня нашей жизни).

То же самое и с Kubernetes. Всё, что происходит в кластере, должно быть записано и сохранено. Вообще всё! И тут на сцену выходит etcd. Эта база данных типа ключ-значение выступает резервным хранилищем для Kubernetes.
</details>

8. Что такое kubelet worker node?
<details>
  <summary>Ответ</summary>
kubelet — это агент, который следит за тем, чтобы на узле всё работало должным образом. Подобная работа подразумевает ряд задач.

Первая — взаимодействие с мастер-узлом. Обычно мастер-узел отправляет задачу в форме манифеста или спецификации (Podspec). Манифест определяет, какие работы необходимо провести и какие Pod’ы нужно создать. 

Вторая — взаимодействие с исполняемой средой контейнера (container runtime) на узле. Исполняемая среда скачивает нужные образы, после чего вступает в действие kubelet, мониторя Pod’ы, созданные с использованием этих образов.

Третья — проверки (probes) состояния Pod’ов. Кто отвечает за них? Конечно же, kubelet! Потому что следить за здоровьем Pod’а — его обязанность!
</details>

9. Что такое kube-proxy worker node?
<details>
  <summary>Ответ</summary>
Следующий неотъемлемый элемент — работа с сетью, и kube-proxy готов позаботиться об этом. Он работает как балансировщик нагрузки, распределяя трафик между Pod’ами, а также следит за соблюдением сетевых правил. Можно сказать, что kube-proxy полностью отвечает за коммуникации внутри кластера.
</details>

10. Что такое container runtime worker node?
<details>
  <summary>Ответ</summary>
Необходим для скачивания нужных образов
</details>

11. Виды манифестов в kubernetes? 
<details>
  <summary>Ответ</summary>
- pod

- deployment

- service

- ingress

- persistent volumes

- persistent volumes claim 
</details>

12. Что такое node в Kubernetes?
<details>
  <summary>Ответ</summary>
 Это физические или виртуальные машины, на которых развертываются и запускаются контейнеры с приложениями. Совокупность нод образует кластер Kubernetes. Nodes бывают двух типов: Master (мастер-нода) — узел, управляющий всем кластером.
</details>


12. Что такое pod в Kubernetes?
<details>
  <summary>Ответ</summary>
Поды — это группы контейнеров, которые совместно используют ресурсы хранения и сетевые ресурсы одного узла. Они создаются с помощью сервера API и размещаются с помощью контроллера.
</details>

13. В чем разница между Init- и Sidecar-контейнерами?
<details>
  <summary>Ответ</summary>
Sidecar-контейнер — это контейнер, который должен быть запущен рядом с основным контейнером внутри пода. Этот паттерн нужен для расширения и улучшения функциональности основного приложения без внесения в него изменений. Представьте, что у вас есть под с одним контейнером, который очень хорошо работает, и вы бы хотели добавить какой-то функционал к этому контейнеру, не внося в него изменений. 

Init-контейнеры -- это специальные контейнеры, которые запускаются при инициализации пода до запуска основных контейнеров. Init-контейнеры подготавливают окружение для работы (выполнение миграций, проверки, склонировать Git-репозиторий, дождаться СУБД или другой сервис, создание конфигов, установка прав на файлы) и могут содержать в себе утилиты, которые не обязательны или не желательны в основном контейнере.

В целом, init-контейнеры работают как обычные контейнеры, за исключением следующих пунктов:

они всегда выполняются до завершения;

каждый init-контейнер должен успешно завершиться, чтобы запустился следующий.

Если init-контейнер завершается с ошибкой, то Kubernetes перезапускает весь под целиком (если, конечно, restartPolicy это позволяет).

</details>


14. Что такое Kubernetes deployment?
<details>
  <summary>Ответ</summary>
Deployment — это объект Kubernetes, представляющий работающее приложение в кластере. При создании объекта Deployment вы можете указать в его поле spec , что хотите иметь три реплики приложения. 
</details>

15. Объясните разницу между pod и deployment?
<details>
  <summary>Ответ</summary>
При создании одного или нескольких контейнеров через pod контейнеры будут в единичном формате а при создании контенеров через deployment есть возможность указать количество репликаций и кубернетис будет удерживать это количество реплик и следить за ними.
</details>

16. В чем разница между Deployment и StatefulSet?
<details>
  <summary>Ответ</summary>

Объект Deployment очень хорош для работы с приложениями, не сохраняющими состояние, а StatefulSets – с сохраняющими. Если вы планируете развертывать приложения, сохраняющие состояние, например, MySQL и Oracle, следует воспользоваться контроллером StatefulSets, а не объектом Deployment.

Контроллер StatefulSets предоставляет возможность пронумеровать все поды по порядку, начиная с нуля. Поэтому при работе с приложениями, сохраняющими состояние, легко обустроить архитектуру, в которой один под является ведущим, а остальные – его репликами.  При этом можно добиться что бы запрос на запись переадресовывался только на первый (ведущий) под, а запрос на считывание переадресовывался на три пода. При этом записанные данные будут синхронизироваться с другими подами. 

Если один из подов погибнет, то заново создается одноименный ему новый под. Эта возможность очень полезна и не нарушает цепочку кластеров с приложениями, сохраняющими состояние. Если же вы масштабируетесь вниз, то избыточные поды удаляются в обратном порядке. 

Резюмируя, обозначим, что StatefulSets обеспечивают следующие преимущества по сравнению с объектами Deployment:

Порядковые номера для каждого из подов.

Первый под может выступать в качестве ведущего, благодаря чему хорошо подходит для подготовки конфигурации с реплицируемой базой данных – такая конфигурация позволяет обрабатывать как чтение, так и запись.

Другие поды действуют в качестве реплик.

Новые поды будут создаваться лишь в случае, если более ранний под сейчас действует, причем, данные более раннего пода клонируются.

Поды удаляются в порядке, обратном тому, в котором создавались
</details>

17. Что такое service?
<details>
  <summary>Ответ</summary>
 Сервис – это абстракция, определяющая набор подов и политику доступа к ним. При создании сервиса будут созданы DNS записи по которым можно будет обращаться с любого Pod -а приложения текущего namespace.
</details>

18. Виды service?
<details>
  <summary>Ответ</summary>
- Cluster IP

- Node Port

- Load Balancer

- External Name 
</details>

19. Что такое clusterIP?
<details>
  <summary>Ответ</summary>
 ClusterIP: Предоставляет Службу на внутреннем IP-адресе кластера. Выбор этого значения делает службу доступной только внутри кластера. Это значение по умолчанию, которое используется, если вы явно не указываете a typeдля службы
</details>

20. Что такое NodePort?
<details>
  <summary>Ответ</summary>
Открытие порта пода для доступа вне кластера.

По умолчанию дается рандомно от 30000-32767

Можно указать в этом диапозоне самому.
</details>

21. Что такое Load Balancer ?
<details>
  <summary>Ответ</summary>
Предоставляет доступ к Службе извне с помощью балансировщика нагрузки облачного провайдера.
</details>

22. Что такое External Name ?
<details>
  <summary>Ответ</summary>
Сопоставляет службу с содержимым поля externalName(например, foo.bar.example.com), возвращая CNAMEзапись с ее значением. Никакого проксирования не настроено.
</details>

23. Что такое namespace?
<details>
  <summary>Ответ</summary>
  Namespace предоставляют механизм изоляции групп ресурсов в пределах одного кластера. Имена ресурсов должны быть уникальными в пространстве имен, но не между пространствами имен. 
</details>

24. Основные команды kubernetes? 
<details>
  <summary>Ответ</summary>
- kubectl apply -f (service, deployment, namespase, ingress, pvc, pv и т.д.) - 	Внести изменения в конфигурацию ресурса из файла или потока stdin

- kubectl get (service, deployment, namespase, ingress, pvc, pv и т.д.) - Вывести один или несколько ресурсов.

- kubectl autoscale - Автоматически промасштабировать набор подов, управляемых контроллером репликации.

- kubectl cluster-info - Показать информацию о главном узле и сервисах в кластере.

- kubectl delete - Удалить ресурсы из файла, потока stdin, либо с помощью селекторов меток, имен, селекторов ресурсов или ресурсов.

- kubectl exec - Выполнить команду в контейнере пода.

- kubectl describe - Показать подробное состояние одного или нескольких ресурсов.

- kubectl logs - Вывести логи контейнера в поде.

</details>

25. Как подключиться к кластеру kubernetes?
<details>
  <summary>Ответ</summary>

Для того, чтобы выполнять команды от текущего пользователя нужно скопировать конфиг администратора кластера.

Создайте каталог в home директории текущего пользователя:

HOME/.kube

Скопируйте конфиг администратора кластера:

/etc/kubernetes/admin.conf $HOME/.kube/config

Выставите права:

HOME/.kube/config

Также этот конфиг можно скопировать напрямую на хост, с которого вы хотите управлять кластером k8s.

</details>

26. Как происходит процес создания нового пода?
<details>
  <summary>Ответ</summary>
При создании нового pod-а – процесс выглядит так:

kubectl шлёт запрос к API-серверу

API-сервер валидирует его, и передаёт в etcd

etcd сообщает обратно API-серверу, что запрос принят и сохранён

API-сервер обращается к kube-scheduler

kube-scheduler определяет ноду(ы), на которой будет создан pod, и возвращает информацию обратно API-серверу

API-сервер отправляет эти данные в etcd

etcd сообщает обратно API-серверу, что запрос принят и сохранён

API-сервер обращается к kubelet на соответствующей ноде(ам)

kubelet обращается к Docker демону (или другому container runtime) через его API через сокет Docker-демона на ноде с задачей запустить контейнер

kubelet отправляет статус pod-а API-серверу

API-сервер обновляет данные в etcd
</details>

27. Какие виды стратегий развертывания есть в kubernetes?
<details>
  <summary>Ответ</summary>
Rolling Strategy Deployment

Recreate

Blue/ Green (or Red / Black) deployments

Canary
</details>

28. Что подразумевается вид развертывания в kubernetes Rolling Strategy Deployment?
<details>
  <summary>Ответ</summary>

Rolling (постепенный, «накатываемый» деплой)

Это стандартная стратегия развертывания в Kubernetes. Она постепенно, один за другим, заменяет pod'ы со старой версией приложения на pod'ы с новой версией — без простоя кластера.

Kubernetes дожидается готовности новых pod'ов к работе (проверяя их с помощью readiness-тестов), прежде чем приступить к сворачиванию старых. Если возникает проблема, подобное накатываемое обновление можно прервать, не останавливая всего кластера.
</details>

29. Что подразумевается вид развертывания в kubernetes Recreate?

<details>
  <summary>Ответ</summary>
Recreate

В этом простейшем типе развертывания старые pod'ы убиваются все разом и заменяются новыми

</details>

30. Что подразумевается вид развертывания в kubernetes Blue/ Green (or Red / Black)?
<details>
  <summary>Ответ</summary>
Blue/ Green (or Red / Black) deployments

Стратегия сине-зеленого развертывания (иногда ее ещё называют red/black, т.е. красно-чёрной) предусматривает одновременное развертывание старой (зеленой) и новой (синей) версий приложения. После размещения обеих версий обычные пользователи получают доступ к зеленой, в то время как синяя доступна для QA-команды для автоматизации тестов через отдельный сервис или прямой проброс портов

После того, как синяя (новая) версия была протестирована и был одобрен ее релиз, сервис переключается на неё, а зеленая (старая) сворачивается
</details>

31. Что подразумевается вид развертывания в kubernetes Canary?
<details>
  <summary>Ответ</summary>
Canary

Канареечные выкаты похожи на сине-зеленые, но лучше управляются и используют прогрессивный поэтапный подход. К этому типу относятся несколько различных стратегий, включая «скрытые» запуски и А/В-тестирование.

Эта стратегия применяется, когда необходимо испытать некую новую функциональность, как правило, в бэкенде приложения. Суть подхода в том, чтобы создать два практически одинаковых сервера: один обслуживает почти всех пользователей, а другой, с новыми функциями, обслуживает лишь небольшую подгруппу пользователей, после чего результаты их работы сравниваются. Если все проходит без ошибок, новая версия постепенно выкатывается на всю инфраструктуру.

Хотя данную стратегию можно реализовать исключительно средствами Kubernetes, заменяя старые pod'ы на новые, гораздо удобнее и проще использовать service mesh вроде Istio.

Например, у вас может быть два различных манифеста в Git: обычный с тегом 0.1.0 и «канареечный» с тегом 0.2.0. Изменяя веса в манифесте виртуального шлюза Istio, можно управлять распределением трафика между этими двумя deployment'ами
</details>

32. Как подключить новую группу нод и удалить старую без потери подов?
<details>
  <summary>Ответ</summary>
Вы можете использовать kubectl drainдля безопасного удаления всех ваших модулей с узла, прежде чем выполнять техническое обслуживание узла (например, обновление ядра, обслуживание оборудования и т. д.). Безопасное выселение позволяет корректно завершать работу контейнеров модуля и будет учитывать указанные вами бюджеты PodDisruptionBudgets.

Успешное завершение kubectl drainозначает, что все модули (кроме тех, которые были исключены, как описано в предыдущем абзаце) были безопасно удалены (с соблюдением желаемого периода постепенного завершения и с соблюдением определенного вами PodDisruptionBudget). После этого можно безопасно отключить узел, выключив его физическую машину или, если он работает на облачной платформе, удалив его виртуальную машину.

Во-первых, определите имя узла, который вы хотите слить. Вы можете перечислить все узлы в вашем кластере с помощью

kubectl get nodes

Затем скажите Kubernetes опустошить узел:

kubectl drain --ignore-daemonsets <node name>

Если есть модули, управляемые DaemonSet, вам нужно будет указать --ignore-daemonsetswith kubectl, чтобы успешно слить узел. Подкоманда kubectl drainсама по себе фактически не истощает узел своих модулей DaemonSet: контроллер DaemonSet (часть плоскости управления) немедленно заменяет отсутствующие модули новыми эквивалентными модулями. Контроллер DaemonSet также создает поды, которые игнорируют незапланированные испорченные данные, что позволяет запускать новые поды на узле, который вы истощаете.

Как только он вернется (без ошибки), вы можете отключить узел (или, что то же самое, если на облачной платформе, удалить виртуальную машину, поддерживающую узел). Если вы оставите узел в кластере во время операции обслуживания, вам нужно запустить

kubectl uncordon <node name>

после этого сообщить Kubernetes, что он может возобновить планирование новых модулей на узле.

  </details>

33. Как настроить модуль для использования ConfigMap? 
<details>
  <summary>Ответ</summary>
https://kubernetes.io/docs/tasks/configure-pod-container/configure-pod-configmap/#configure-all-key-value-pairs-in-a-configmap-as-container-environment-variables
  </details>

34.
 <details>
  <summary>Ответ</summary>

   </details>

35. Какие CNI вы использовали и чем они отличаются?
 <details>
  <summary>Ответ</summary>
1. Calico
Тип: Stateful, поддерживает как оверлейные, так и андерлейные сети.
Особенности:
Поддерживает сетевые политики и безопасность.
Использует BGP для маршрутизации трафика, что позволяет масштабировать сети.
Может работать без оверлея, что упрощает конфигурацию и повышает производительность.
2. Flannel
Тип: Оверлейная сеть.
Особенности:
Простой в настройке и использовании.
Использует VXLAN или другие механизмы для инкапсуляции трафика.
Не поддерживает сложные сетевые политики, что может быть ограничением для более сложных сценариев.
   </details>

36. Чем отличается managed Kubernetes от self-deployed?
 <details>
  <summary>Ответ</summary>
Managed Kubernetes и self-deployed (или self-managed) Kubernetes представляют собой два различных подхода к развертыванию и управлению кластерами Kubernetes. Вот основные различия между ними:
1. Управление и поддержка
Managed Kubernetes:
Кластеры управляются облачным провайдером, который берет на себя ответственность за настройку, обновление, мониторинг и обслуживание control plane (управляющего уровня).
Пользователи получают доступ к кластеру через API и инструменты управления, такие как kubectl, но не имеют доступа к мастер-нодам.
Провайдеры обеспечивают отказоустойчивость и автоматизацию, что позволяет пользователям сосредоточиться на разработке приложений.
Self-deployed Kubernetes:
Кластеры настраиваются и управляются внутренними командами IT или DevOps. Это может происходить на виртуальных машинах или выделенных серверах.
Полный контроль над конфигурацией кластера, включая доступ к мастер-нодам, что позволяет гибко настраивать инфраструктуру под специфические требования.
Ответственность за обновления, безопасность и мониторинг лежит на команде, что требует наличия соответствующих навыков и ресурсов.
2. Уровень кастомизации
Managed Kubernetes:
Ограниченная возможность настройки, так как многие аспекты управления кластером контролируются провайдером. Пользователи могут добавлять настройки через API или конфигурационные файлы, но в рамках заданных ограничений.
Self-deployed Kubernetes:
Высокая степень кастомизации. Пользователи могут настроить кластер в соответствии с конкретными потребностями бизнеса, включая сетевые настройки, безопасность и интеграцию с другими системами.
3. Затраты времени и ресурсов
Managed Kubernetes:
Быстрое развертывание: пользователи могут создать кластер всего за несколько минут через веб-интерфейс или командную строку.
Меньше времени уходит на управление инфраструктурой, что позволяет сосредоточиться на разработке приложений.
Self-deployed Kubernetes:
Требует значительных временных затрат на настройку и управление. Необходимость в квалифицированных специалистах для поддержки кластера.
Время на развертывание может быть значительно больше, особенно если требуется сложная настройка.
4. Стоимость
Managed Kubernetes:
Обычно стоит дороже из-за включенных услуг управления и поддержки от провайдера.
Self-deployed Kubernetes:
Может быть более экономичным решением, особенно для крупных организаций с уже существующей инфраструктурой.
   </details>

37. Как можно контролировать размещение подов в кластере? (taints/tolerations, affinities, topologies etc.)
 <details>
  <summary>Ответ</summary>
1. nodeSelector
Описание: Это самый простой метод управления размещением подов. В спецификации пода указывается поле nodeSelector, в котором перечисляются метки узлов, соответствующие требованиям пода.
Пример:
text
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  nodeSelector:
    storage: ssd
  containers:
  - name: my-container
    image: my-image
Использование: Поды будут запланированы только на узлах, имеющих метку storage=ssd.
2. Affinity и Anti-affinity
Описание: Позволяют более гибко управлять размещением подов на основе правил совместного или раздельного существования.
Типы:
Pod Affinity: Позволяет размещать поды на узлах с другими подами, которые соответствуют определенным меткам.
Pod Anti-affinity: Запрещает размещение подов на узлах, где уже работают другие поды с определенными метками.
Пример:
text
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  affinity:
    podAffinity:
      requiredDuringSchedulingIgnoredDuringExecution:
        labelSelector:
          matchExpressions:
            - key: app
              operator: In
              values:
                - my-app
        topologyKey: "kubernetes.io/hostname"
  containers:
  - name: my-container
    image: my-image
Использование: Этот метод позволяет более точно контролировать размещение подов в зависимости от их взаимодействия и требований к ресурсам.
3. nodeName
Описание: В спецификации пода можно указать конкретный узел, на котором должен быть запущен под, с помощью поля nodeName.
Пример:
text
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  nodeName: node01
  containers:
  - name: my-container
    image: my-image
Использование: Этот метод подходит для случаев, когда необходимо жестко привязать под к конкретному узлу.
4. Топологические ограничения (Topology Spread Constraints)
Описание: Позволяют контролировать распределение подов по различным топологическим доменам (например, зонам доступности).
Пример:
text
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  template:
    spec:
      topologySpreadConstraints:
      - maxSkew: 1
        topologyKey: "kubernetes.io/hostname"
        whenUnsatisfiable: DoNotSchedule
        labelSelector:
          matchLabels:
            app: my-app
      containers:
      - name: my-container
        image: my-image
Использование: Это позволяет избежать ситуации, когда все поды одного приложения размещаются на одном узле или в одной зоне доступности.
   </details>

38. Скейлинг кластера. Cluster autoscaler vs HPA vs VPA? 
 <details>
  <summary>Ответ</summary>
1. Horizontal Pod Autoscaler (HPA)
Описание: HPA автоматически изменяет количество реплик подов в зависимости от текущей нагрузки, основываясь на метриках, таких как использование CPU или памяти.
Принцип работы: HPA следит за заданными метриками и увеличивает или уменьшает количество подов для достижения целевого уровня использования ресурсов.
Использование: Подходит для приложений с переменной нагрузкой, где необходимо быстро реагировать на изменения в трафике.
2. Vertical Pod Autoscaler (VPA)
Описание: VPA автоматически изменяет ресурсы (CPU и память) для существующих подов, чтобы лучше соответствовать их потребностям.
Принцип работы: VPA анализирует использование ресурсов подами и вносит изменения в их конфигурацию, что может включать перезапуск подов с новыми параметрами.
Использование: Идеален для приложений с изменяющимися требованиями к ресурсам, где важно оптимизировать использование ресурсов без добавления новых подов.
3. Cluster Autoscaler
Описание: Cluster Autoscaler автоматически изменяет количество узлов в кластере в зависимости от потребностей в ресурсах.
Принцип работы: Если есть поды, которые не могут быть запланированы из-за нехватки ресурсов, Cluster Autoscaler добавляет новые узлы. Если узлы не используются длительное время, они могут быть удалены.
Использование: Полезен для управления масштабируемостью кластера и обеспечения достаточных ресурсов для HPA и VPA.

39. Как сделать zero-downtime node decommission/cluster upgrade? PDB? Lifecycle hooks?
 <details>
  <summary>Ответ</summary>
Для достижения zero-downtime при деактивации узлов (node decommission) или обновлении кластера в Kubernetes можно использовать несколько методов и механизмов. Основные из них включают Pod Disruption Budgets (PDB), Lifecycle Hooks и правильное управление обновлениями и дренированием узлов.
1. Pod Disruption Budgets (PDB)
PDB позволяет контролировать количество одновременно недоступных подов при проведении операций обслуживания, таких как дренирование узлов. С помощью PDB вы можете установить минимальное количество подов, которые должны оставаться доступными во время операций, что помогает предотвратить ситуации с недоступностью сервиса.
Пример настройки PDB:
text
apiVersion: policy/v1beta1
kind: PodDisruptionBudget
metadata:
  name: my-app-pdb
spec:
  minAvailable: 1
  selector:
    matchLabels:
      app: my-app
Это правило гарантирует, что как минимум один под вашего приложения всегда будет доступен, даже если вы дренируете узел.
2. Lifecycle Hooks
Lifecycle Hooks позволяют выполнять определенные действия перед завершением работы пода или его запуском. Это может быть полезно для корректного завершения процессов или освобождения ресурсов.
Пример использования PreStop Hook:
text
lifecycle:
  preStop:
    exec:
      command: ["/bin/sh", "-c", "sleep 10"]
Этот hook задерживает завершение пода на 10 секунд, что позволяет завершить активные соединения и запросы, минимизируя риск потери данных.
3. Дренирование узлов
При дренировании узлов важно следовать правильной последовательности действий:
Cordon узел: Это предотвратит планирование новых подов на узле.
bash
kubectl cordon <node-name>
Drain узел: Используйте команду kubectl drain, чтобы удалить поды с узла. Убедитесь, что у вас настроены PDB для управления количеством доступных подов.
bash
kubectl drain <node-name> --ignore-daemonsets --delete-local-data
Обновление или обслуживание узла: После успешного дренирования вы можете выполнять необходимые операции.
Возврат узла в кластер: После завершения обслуживания используйте команду kubectl uncordon, чтобы вернуть узел в кластер.
bash
kubectl uncordon <node-name>
   </details>

40. С каким PID запускается процесс в контейнере?
 <details>
  <summary>Ответ</summary>
В контейнере процесс, который запускается первым, получает PID 1 (идентификатор процесса). Это важно, так как процесс с PID 1 управляет жизненным циклом контейнера. Если этот процесс завершится, контейнер также будет остановлен.
   </details>

41. Что происходит в Kubernetes после запуска kubectl (API, ReplicaSet Controller, storage back-end, scheduler, kubelet, worker node, pod)?
 <details>
  <summary>Ответ</summary>

   </details>

42. Какая разница между pod и контейнером в K8s?
 <details>
  <summary>Ответ</summary>

   </details>

43. Как мы можем сделать любой микросервис, работающий на K8s, доступным из внешней среды?
 <details>
  <summary>Ответ</summary>

   </details>