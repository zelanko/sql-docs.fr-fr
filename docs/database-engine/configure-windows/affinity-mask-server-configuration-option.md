---
title: affinity mask (option de configuration de serveur)
description: Découvrez-en plus sur l’option de masque d’affinité dans SQL Server. Affichez un exemple qui l’utilise pour lier les processeurs à des threads spécifiques.
ms.prod: sql
ms.prod_service: high-availability
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default affinity mask option
- reloading processor cache
- processor cache [SQL Server]
- CPU [SQL Server], licensing
- deferred process call
- affinity mask option
- processor affinity [SQL Server]
- SMP
- DPC
ms.assetid: 5823ba29-a75d-4b3e-ba7b-421c07ab3ac1
author: markingmyname
ms.author: maghan
ms.reviewer: mikeray
ms.custom: ''
ms.date: 06/11/2020
ms.openlocfilehash: 94f8406af013bc0720bc16063d1a9881eda94c5a
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715592"
---
# <a name="affinity-mask-server-configuration-option"></a>affinity mask (option de configuration de serveur)

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

> [!NOTE]
> [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] Utilisez plutôt [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md).

Pour réaliser les travaux multitâches, [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows déplace parfois les threads de processus entre les différents processeurs. Bien qu’efficace du point de vue du système d’exploitation, cette activité peut réduire les performances de SQL Server sous des charges de système intenses, car des données sont rechargées de façon répétée dans chaque cache de processeur. L'affectation de processeurs à des threads spécifiques peut améliorer les performances sous ces conditions en éliminant les rechargements de processeur et en réduisant la migration de threads sur l’ensemble des processeurs, ce qui réduit le changement de contexte. Une telle association entre un thread et un processeur est appelée affinité du processeur.

SQL Server prend en charge l’affinité du processeur au moyen de deux options de masque d’affinité : affinity mask (également appelé CPU **affinity mask**) et affinity I/O mask. Pour plus d’informations sur l’option affinity I/O mask, consultez [affinity Input-Output mask (option de configuration de serveur)](../../database-engine/configure-windows/affinity-input-output-mask-server-configuration-option.md). La prise en charge de l’affinité du processeur et d’E/S pour les serveurs dotés de 33 à 64 processeurs nécessite l’utilisation supplémentaire de l’[option de configuration de serveur affinity64 mask](../../database-engine/configure-windows/affinity64-mask-server-configuration-option.md) et de l’[option de configuration du serveur affinity64 Input-Output mask](../../database-engine/configure-windows/affinity64-input-output-mask-server-configuration-option.md), respectivement.

> [!NOTE]  
> La prise en charge de l'affinité pour les serveurs dotés de 33 à 64 processeurs est uniquement disponible sur les systèmes d'exploitation 64 bits.

L'option affinity mask, qui existait dans les versions antérieures de SQL Server, contrôle dynamiquement l'affinité du processeur.

Dans SQL Server, l'option affinity mask peut être configurée sans exiger le redémarrage de l'instance de SQL Server. Lorsque vous utilisez sp_configure, vous devez exécuter RECONFIGURE ou RECONFIGURE WITH OVERRIDE après la définition d'une option de configuration. Si vous utilisez [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)], la modification de l'option de masque d'affinité ne nécessite aucun redémarrage.

Les modifications apportées aux masques d'affinité s'exécutent dynamiquement, autorisant ainsi le démarrage et l'arrêt à la demande des planificateurs de processeur qui lient les threads de processus au sein de SQL Server. Cela peut se produire en cas de changement des conditions sur le serveur. Par exemple, si une nouvelle instance de SQL Server est ajoutée au serveur, il peut être nécessaire d'ajuster l'option affinity mask afin de redistribuer la charge des processeurs.

Les modifications apportées aux masques de bits d'affinité nécessitent que SQL Server active un nouveau planificateur de processeur et désactive le planificateur de processeur existant. Les nouveaux traitements peuvent alors être traités sur le nouveau planificateur ou sur les planificateurs restants.

Pour lancer un nouveau planificateur de processeur, SQL Server crée un nouveau planificateur et l'ajoute à la liste de ses planificateurs standard. Le nouveau planificateur n'est pris en compte que pour les nouveaux traitements entrants. Les traitements en cours continuent de s'exécuter sur le même planificateur. Les threads de travail migrent vers le nouveau planificateur lorsqu'ils sont libérés, ou lorsque de nouveaux threads de travail sont créés.

L'arrêt d'un planificateur exige l'achèvement et la clôture des activités de tous les traitements sur le planificateur. Un planificateur arrêté est marqué hors ligne afin qu'aucun nouveau traitement ne soit planifié sur celui-ci.

Qu'un nouveau planificateur soit ajouté ou supprimé, les tâches système permanentes, telles que lock monitor, checkpoint, system task thread (processing DTC) et signal process, continuent de s'exécuter sur le planificateur alors que le serveur est opérationnel. Ces tâches système permanentes ne migrent pas dynamiquement. Si vous souhaitez redistribuer la charge des processeurs pour ces tâches systèmes entre les planificateurs, il est nécessaire de redémarrer l'instance de SQL Server. Si SQL Server tente d'arrêter un planificateur associé à une tâche système permanente, la tâche continue de s'exécuter sur le planificateur hors ligne (aucune migration). Ce planificateur est lié aux processeurs dans le masque d'affinité modifié et n’impose aucune charge au processeur avec lequel il était lié avant la modification. Le fait de disposer de planificateurs hors ligne supplémentaires n'affecte pas vraiment la charge du système. Si c’est le cas, un redémarrage du serveur de base de données est nécessaire pour reconfigurer ces tâches sur les planificateurs disponibles avec le masque d’affinité modifié.

Ne définissez pas les valeurs de configuration « affinity mask » et « affinity I/O mask » de SQL Server pour utiliser les mêmes processeurs. Les performances peuvent être affectées si vous choisissez de lier un processeur pour la planification des threads de travail SQL Server et pour le traitement des E/S. Par conséquent, assurez-vous que les valeurs de configuration ne sont pas définies pour le même processeur. La même recommandation s’applique à 'affinity64 mask' et à 'affinity64 I/O mask'.  Pour vous assurer que le masque d'affinité ne chevauche pas le masque d’E/S d’affinité, la commande [RECONFIGURE](../../t-sql/language-elements/reconfigure-transact-sql.md) vérifie que les affinités du processeur et d'E/S normales s'excluent mutuellement. Sinon, un message d'erreur est envoyé à la session cliente et consigné dans le journal des erreurs SQL Server pour indiquer qu'un tel paramètre n'est pas recommandé.

```sql
 Msg 5834, Level 16, State 1, Line 1
 The affinity mask specified conflicts with the IO affinity mask specified. Use the override option to force this configuration
```

L'exécution des options RECONFIGURE WITH OVERRIDE autorise les affinités du processeur et celles d'E/S à se chevaucher et à ne pas s'exclure pas mutuellement.  

Les tâches d'affinité d'E/S (telles que lazy writer et log writer) sont directement affectées par le masque d'affinité d'E/S. Si les tâches lazy writer et log writer ne sont pas liées, elles respectent les mêmes règles que celles définies pour les tâches permanentes telles que lock monitor ou checkpoint.
Si vous spécifiez un masque d'affinité qui tente d'effectuer un mappage à un processeur inexistant, la commande RECONFIGURE envoie un message d'erreur à la session cliente et le consigne dans le journal des erreurs SQL Server. L'utilisation de l'option RECONFIGURE WITH OVERRIDE n'a aucun effet dans ce cas, et la même erreur de configuration est à nouveau signalée.

Vous pouvez également exclure l'activité propre à SQL Server des affectations de charges de travail spécifiques par le système d'exploitation Windows. En attribuant la valeur 1 à un bit qui représente un processeur, ce processeur est sélectionné par le moteur de base de données SQL Server pour l'affectation des threads. Si vous attribuez la valeur 0 (valeur par défaut) à l’option **affinity mask**, les algorithmes de planification de Microsoft Windows 2000 définissent l’affinité du thread. Si vous attribuez à **affinity mask** une valeur différente de zéro, l’affinité SQL Server interprète cette valeur comme étant un masque de bits indiquant que ces processeurs sont ceux sur lesquels doit porter la sélection.  

La non-exécution des threads SQL Server sur des processeurs particuliers permet à Microsoft Windows 2000 ou Windows Server 2003 de mieux évaluer la gestion par le système de traitement des processus propres à Windows. Par exemple, sur un serveur à 8 processeurs exécutant deux instances de SQL Server (instances A et B), l'administrateur système peut utiliser l'option affinity mask pour affecter le premier jeu de 4 processeurs à l'instance A et le deuxième jeu de 4 processeurs à l'instance B. Pour configurer plus de 32 processeurs, définissez à la fois affinity mask et affinity64 mask. Les valeurs de l’option **affinity mask** sont les suivantes :

- Un masque **affinity mask** à un octet prend en charge jusqu’à huit processeurs sur un ordinateur multiprocesseur.

- Un masque **affinity mask** à deux octets prend en charge jusqu’à 16 processeurs sur un ordinateur multiprocesseur.

- Un masque **affinity mask** à trois octets prend en charge jusqu’à 24 processeurs sur un ordinateur multiprocesseur.

- Un masque **affinity mask** à quatre octets prend en charge jusqu’à 32 processeurs sur un ordinateur multiprocesseur.

- Si vous disposez de plus de 32 processeurs, configurez un masque d'affinité à quatre octets pour les 32 premiers processeurs et un masque d'affinity64 à quatre octets pour les processeurs restants.

Étant donné que la définition de l'affinité du processeur de SQL Server est une opération spécialisée, il est recommandé de n'utiliser cette option que lorsque cela est véritablement nécessaire. Dans la plupart des cas, l'option d'affinité par défaut de Microsoft Windows 2000 offre des performances optimales. Lors de la définition des masques d'affinité, tenez également compte des exigences des autres applications en matière de processeurs. Pour plus d'informations, consultez la documentation du système d'exploitation Windows.

> [!NOTE]
> Vous pouvez utiliser le Moniteur système Windows pour afficher et analyser l'utilisation des processeurs individuels.

Lorsque vous spécifiez l’option affinity I/O mask, vous devez l’utiliser avec l’option de configuration affinity mask. Cependant, comme mentionné précédemment, évitez d’activer sur le même processeur le commutateur **affinity mask** et l’option affinity I/O mask. Les bits correspondant à chaque processeur doivent être dans l'un des trois états suivants :

- 0 dans l'option affinity mask et dans l'option affinity I/O mask.

- 1 dans l'option affinity mask et 0 dans l'option affinity I/O mask.

- 0 dans l'option affinity mask et 1 dans l'option affinity I/O mask.

> [!CAUTION]
> Évitez de configurer l'affinité de processeur dans le système d'exploitation Windows et le masque d'affinité dans SQL Server. Ces paramètres tentent d'obtenir le même résultat et, si les configurations sont incohérentes, les résultats risquent d'être imprévisibles. Il est préférable de configurer l’affinité de processeur SQL Server à l’aide de l’option sp_configure dans SQL Server.

## <a name="example"></a>Exemple

Par exemple, pour définir l'option affinity mask, si les processeurs 1, 2 et 5 sont sélectionnés comme étant disponibles et si les bits aux positions 1, 2 et 5 ont la valeur 1 alors que les bits 0, 3, 4, 6 et 7 ont la valeur 0, une valeur hexadécimale égale à 0x26 ou l'équivalent décimal 38 est spécifiée. Numérotez les positions des bits de droite à gauche.

```sql
sp_configure 'show advanced options', 1;
RECONFIGURE;
GO
sp_configure 'affinity mask', 38;
RECONFIGURE;
GO
```

Vous trouverez ci-dessous les valeurs de l’option **affinity mask** pour un système à huit processeurs.  

|Valeur décimale|Masque binaire|Autorise les threads SQL Server sur les processeurs|  
|-------------------|---------------------|--------------------------------------------|  
|1|00000001|0|  
|3|00000011|0 et 1|  
|7|00000111|0, 1 et 2|  
|15|00001111|0, 1, 2 et 3|  
|31|00011111|0, 1, 2, 3 et 4|  
|63|00111111|0, 1, 2, 3, 4 et 5|  
|127|01111111|0, 1, 2, 3, 4, 5 et 6|  
|255|11111111|0, 1, 2, 3, 4, 5, 6 et 7|  

L'option affinity mask est une option avancée. Si vous utilisez la procédure stockée système sp_configure pour changer sa valeur, vous ne pouvez modifier l’option **affinity mask** que si la valeur 1 a été attribuée à l’option **show advanced options** . Après l'exécution de la commande [!INCLUDE[tsql](../../includes/tsql-md.md)] RECONFIGURE, le nouveau paramètre prend immédiatement effet sans redémarrage de l'instance SQL Server.  

## <a name="non-uniform-memory-access-numa"></a>Non-uniform memory access (NUMA)

Lorsque vous utilisez l'accès NUMA (Non-uniform memory access) matériel et que le masque d'affinité est défini, chaque planificateur dans un nœud est lié à son propre processeur. Lorsque le masque d'affinité n'est pas défini, chaque planificateur est lié au groupe de processeurs au sein du nœud NUMA et un planificateur mappé sur le nœud NUMA N1 peut planifier du travail sur tout processeur dans le nœud, mais pas sur des processeurs associés à un autre nœud.  

Toute opération en cours sur un nœud NUMA unique peut utiliser uniquement des pages tampon à partir de ce nœud. Lorsqu'une opération est exécutée en parallèle sur des unités centrales issues de plusieurs nœuds, de la mémoire peut être utilisée à partir de tout nœud impliqué.  
  
## <a name="licensing-issues"></a>À propos des licences

L'affinité dynamique dépend étroitement des licences des processeurs. SQL Server n'autorise pas la configuration d'options de masque d'affinité qui enfreignent la stratégie de licences.  

### <a name="startup"></a>Démarrage

Si un masque d'affinité spécifié ne respecte pas la stratégie de licences au moment du démarrage de SQL Server ou de l'attachement de la base de données, la couche du moteur achève le processus de démarrage ou l'opération de restauration/attachement de base de données, puis remet à zéro la valeur d'exécution sp_configure du masque d'affinité, en consignant un message d'erreur dans le journal des erreurs SQL Server.  
  
### <a name="reconfigure"></a>Reconfigurer

Si un masque d'affinité spécifié ne respecte pas la stratégie de licences lors de l'exécution de la commande [!INCLUDE[tsql](../../includes/tsql-md.md)] RECONFIGURE, un message d'erreur est envoyé à la session cliente et est consigné dans le journal des erreurs SQL Server, exigeant ainsi que l'administrateur de la base de données reconfigure le masque d'affinité. Aucune commande RECONFIGURE WITH OVERRIDE n'est acceptée dans ce cas.  

## <a name="next-steps"></a>Étapes suivantes

- [Analyser l’utilisation des ressources &#40;Moniteur système&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)
- [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)
- [Options de configuration de serveur &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)
- [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)
- [ALTER SERVER CONFIGURATION &#40;Transact-SQL&#41;](../../t-sql/statements/alter-server-configuration-transact-sql.md)
