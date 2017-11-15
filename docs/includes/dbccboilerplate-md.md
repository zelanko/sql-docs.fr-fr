Recherchez une défaillance matérielle, exécutez les diagnostics matériels et corrigez les problèmes rencontrés. Examinez également les journaux système et des applications Windows, ainsi que le journal des erreurs de SQL Server, pour vérifier si l'erreur est due à une défaillance matérielle. Corrigez les éventuels problèmes matériels contenus dans les journaux.

Si vous avez des problèmes persistants de données endommagées, tentez d'échanger votre ordinateur, vos contrôleurs et vos lecteurs de disque contre d'autres composants. Assurez-vous que la mise en cache des écritures n’est pas activée sur le contrôleur de disque de votre système. Si vous soupçonnez que c’est la cause du problème, contactez votre fournisseur de matériel.

Enfin, il peut s'avérer bénéfique d'utiliser un matériel totalement nouveau, avec reformatage des lecteurs de disque et réinstallation du système d'exploitation.

Restaurer à partir d’une sauvegarde : s’il ne s’agit pas d’un problème de matériel et qu’une sauvegarde propre est disponible, restaurez la base de données à partir de cette sauvegarde.

Exécuter DBCC CHECKDB : si aucune sauvegarde propre n’est disponible, exécutez DBCC CHECKDB sans clause REPAIR pour déterminer l’étendue de l’altération. DBCC CHECKDB recommande une clause REPAIR à utiliser. Puis, exécutez DBCC CHECKDB avec la clause REPAIR adéquate afin de réparer les dommages.

> **balise d’alerte non prise en charge !**
> **balise tr non prise en charge !**
> **balise tr non prise en charge !**

Si l'exécution de DBCC CHECKDB avec une des clauses REPAIR ne résout pas le problème, contactez l’assistance technique.

