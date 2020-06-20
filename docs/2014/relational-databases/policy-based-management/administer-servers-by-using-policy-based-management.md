---
title: Administrer des serveurs à l’aide de la Gestion basée sur des stratégies | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- facet See facets
- Declarative Management Framework See Policy-Based Management
- surface area configuration [SQL Server], Policy-Based Management
- Policy-Based Management
- facets [Policy-Based Management]
- Policy-Based Management, administering
- conditions [Policy-Based Management]
- facets [Policy-Based Management], about facets
- PolicyAdministratorRole role
ms.assetid: ef2a7b3b-614b-405d-a04a-2464a019df40
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c0f415ffbc10b93cee2037da78daef3b7ee5aba9
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85069026"
---
# <a name="administer-servers-by-using-policy-based-management"></a>Administrer des serveurs à l'aide de la Gestion basée sur des stratégies
  La Gestion basée sur des stratégies est un système permettant de gérer une ou plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Lorsque les administrateurs de stratégie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisent la Gestion basée sur des stratégies, ils utilisent [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] pour créer des stratégies afin de gérer des entités sur le serveur, telles que l'instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les bases de données ou les autres objets [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="benefits-of-policy-based-management"></a>Avantages offerts par la Gestion basée sur des stratégies  
 La Gestion basée sur des stratégies est utile pour résoudre les problèmes présentés dans les scénarios suivants :  
  
-   Une stratégie d'entreprise interdit l'activation de la Messagerie de base de données ou de SQL Mail. Une stratégie est créée afin de vérifier l'état du serveur pour ces deux fonctionnalités. Un administrateur compare l'état du serveur à la stratégie. Si l'état du serveur est hors de conformité, l'administrateur choisit le mode Configurer et la stratégie met l'état du serveur en conformité.  
  
-   La base de données [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] a une convention d'affectation des noms qui requiert que toutes les procédures stockées commencent par les lettres AW_. Une stratégie est créée afin d'appliquer cette stratégie. Un administrateur teste cette stratégie et reçoit une liste des procédures stockées qui sont hors de conformité. Si les futures procédures stockées ne sont pas conformes à cette convention d'affectation des noms, les instructions de création des procédures stockées échouent.  
  
> [!NOTE]  
>  Sachez que les stratégies peuvent affecter le fonctionnement des fonctionnalités [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Par exemple, la capture des données modifiées et la réplication transactionnelle utilisent toutes deux la table systranschemas, qui n'a pas d'index. Si vous activez une stratégie stipulant que toutes les tables doivent avoir un index, la mise en conformité à cette stratégie entraînera l'échec de ces fonctionnalités.  
  
 Les stratégies sont créées et gérées à l'aide de [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]. Le processus comporte les étapes suivantes :  
  
1.  Sélectionner une facette de la Gestion basée sur des stratégies qui contient les propriétés à configurer.  
  
2.  Définir une condition qui spécifie l'état d'une facette de gestion.  
  
3.  Définir une stratégie qui contient la condition, des conditions supplémentaires qui filtrent les jeux de cibles et le mode d'évaluation.  
  
4.  Vérifier si une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est conforme à la stratégie.  
  
 Pour les stratégies qui échouent, l'Explorateur d'objets indique un état critique sous forme d'icône rouge à côté de la cible et des nœuds situés plus hauts dans l'arborescence de l'Explorateur d'objets.  
  
> [!NOTE]  
>  Lorsque le système calcule le jeu d'objets pour une stratégie, les objets système sont exclus par défaut.  Par exemple, si le jeu d'objets de la stratégie fait référence à toutes les tables, la stratégie ne s'applique pas aux tables système. Si les utilisateurs souhaitent évaluer une stratégie sur les objets système, ils peuvent les ajouter explicitement au jeu d'objets. Toutefois, bien que toutes les stratégies soient prises en charge pour le mode d'évaluation **vérifier la planification** , pour des raisons de performances, toutes les stratégies comportant des jeux d'objets arbitraires ne sont pas prises en charge pour le mode d'évaluation **vérifier la planification** . Pour plus d’informations, consultez.[https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx](https://blogs.msdn.com/b/sqlpbm/archive/2009/04/13/policy-evaluation-modes.aspx)  
  
## <a name="policy-based-management-concepts"></a>Concepts de Gestion basée sur des stratégies  
 La Gestion basée sur des stratégies a trois composants :  
  
-   Gestion des stratégies  
  
     Les administrateurs de stratégie créent des stratégies.  
  
-   Administration explicite  
  
     Les administrateurs sélectionnent une ou plusieurs cibles gérées et vérifient de manière explicite que celles-ci sont conformes à une stratégie spécifique, ou rendent de manière explicite les cibles conformes à une stratégie.  
  
-   Modes d'évaluation  
  
     Il existe quatre modes d'évaluation, dont trois peuvent être automatisés :  
  
    -   **À la demande**. Ce mode évalue la stratégie lorsqu'elle est spécifiée directement par l'utilisateur.  
  
    -   **En cas de modification : empêcher**. Ce mode automatisé utilise des déclencheurs DDL pour empêcher les violations de stratégie.  
  
        > [!IMPORTANT]  
        >  Si l’option de configuration serveur relative aux déclencheurs imbriqués (nested triggers) est désactivée, le mode **Sur modification : empêcher** ne fonctionne pas correctement. La Gestion basée sur des stratégies repose sur des déclencheurs DDL pour détecter et restaurer les opérations DDL qui ne sont pas conformes aux stratégies qui utilisent ce mode d'évaluation. Si les déclencheurs DDL de la Gestion basée sur des stratégies est supprimée ou si les déclencheurs imbriqués sont désactivés, ce mode d'évaluation échouera ou se comportera de façon inattendue.  
  
    -   **Sur modification : Journal uniquement**. Ce mode automatisé utilise la notification d'événements pour évaluer une stratégie lorsqu'une modification pertinente est apportée.  
  
    -   **Selon planification**. Ce mode automatisé utilise un travail de l'agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour évaluer périodiquement une stratégie.  
  
     Lorsque les stratégies automatisées ne sont pas activées, la Gestion basée sur des stratégies n'affecte pas les performances système.  
  
## <a name="policy-based-management-terms"></a>Termes relatifs à la Gestion basée sur des stratégies  
 Cible gérée de la Gestion basée sur des stratégies  
 Entités gérées par la Gestion basée sur des stratégies, telles qu'une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], une base de données, une table ou un index. Toutes les cibles dans une instance de serveur forment une hiérarchie cible. Un jeu de cibles est l'ensemble des cibles qui résulte de l'application d'un jeu de filtres cibles à la hiérarchie cible, par exemple toutes les tables de la base de données détenues par le schéma HumanResources.  
  
 Facette de la Gestion basée sur des stratégies  
 Ensemble de propriétés logiques qui modèlent le comportement ou les caractéristiques de certains types de cibles gérées. Le nombre et les caractéristiques des propriétés sont intégrés à la facette et peuvent être ajoutés ou supprimés uniquement par le créateur de la facette. Un type de cible peut implémenter une ou plusieurs facettes de gestion et une facette de gestion peut être implémentée par un ou plusieurs types de cibles. Certaines propriétés d'une facette peuvent s'appliquer uniquement à une version spécifique.  
  
 Condition de la Gestion basée sur des stratégies  
 Expression booléenne qui spécifie un ensemble d'états autorisés pour une cible gérée par la Gestion basée sur des stratégies en ce qui concerne une facette de gestion. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tente d’observer les classements au moment de l’évaluation d’une condition. Si les classements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne correspondent pas exactement aux classements Windows, testez votre condition afin de déterminer la façon dont l'algorithme résout les conflits.  
  
 Stratégie de la Gestion basée sur des stratégies  
 Condition de la Gestion basée sur des stratégies et comportement attendu, par exemple mode d'évaluation, filtres de cibles et planification. Une stratégie ne peut contenir qu'une seule condition. Les stratégies peuvent être activées ou désactivées. Les stratégies sont stockées dans la base de données msdb.  
  
 Catégorie de la stratégie de la Gestion basée sur des stratégies  
 Catégorie définie par l'utilisateur afin d'aider à gérer les stratégies. Les utilisateurs peuvent classifier les stratégies en différentes catégories de stratégies. Une stratégie appartient à une seule catégorie de stratégie. Les catégories de stratégies s'appliquent aux bases de données et aux serveurs. Au niveau de la base de données, les conditions suivantes s'appliquent :  
  
-   Les propriétaires de base de données peuvent abonner une base de données à un jeu de catégories de stratégies.  
  
-   Seules les stratégies de ses catégories abonnées peuvent gouverner une base de données.  
  
-   Toutes les bases de données sont abonnées implicitement à la catégorie de stratégie par défaut.  
  
 Au niveau du serveur, les catégories de stratégies peuvent être appliquées à toutes les bases de données.  
  
 Stratégie actuelle  
 Les stratégies actuelles d'une cible sont celles qui gouvernent cette cible. Une stratégie est actuelle en ce qui concerne une cible uniquement si toutes les conditions suivantes sont remplies :  
  
-   La stratégie est activée.  
  
-   La cible appartient au jeu de cibles de la stratégie.  
  
-   La cible ou l'un de ses ancêtres s'abonne au groupe de stratégies qui contient cette stratégie.  
  
## <a name="policy-based-management-tasks"></a>Tâches de Gestion basée sur des stratégies  
 La Gestion basée sur des stratégies est un système de stratégies permettant de gérer une ou plusieurs instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Utilisez la Gestion basée sur des stratégies pour créer des conditions qui contiennent des expressions de condition. Ensuite, créez des stratégies qui appliquent les conditions à des objets cibles de base de données.  
  
|Description de la tâche|Rubrique|  
|----------------------|-----------|  
|Décrit comment les stratégies de Gestion basée sur des stratégies sont stockées.|Stockage de Gestion basée sur des stratégies|  
|Décrit comment configurer des alertes afin d'informer les administrateurs de stratégie en cas d'échec de stratégie.|[Configurer des alertes afin d'informer les administrateurs de stratégie en cas d'échec de stratégie](configure-alerts-to-notify-policy-administrators-of-policy-failures.md)|  
|Décrit comment créer, afficher, modifier et supprimer une condition de Gestion basée sur des stratégies.|[Créer une condition de gestion basée sur des stratégies.](create-a-new-policy-based-management-condition.md)<br /><br /> [Supprimer une condition de gestion basée sur des stratégies.](delete-a-policy-based-management-condition.md)<br /><br /> [Afficher ou modifier les propriétés d'une condition de gestion basée sur des stratégies](view-or-modify-the-properties-of-a-policy-based-management-condition.md)|  
|Décrit comment créer, afficher, modifier et supprimer une stratégie de Gestion basée sur des stratégies.|[Créer une stratégie de gestion basée sur des stratégies](create-a-policy-based-management-policy.md)<br /><br /> [Supprimer une stratégie de gestion basée sur des stratégies](delete-a-policy-based-management-policy.md)<br /><br /> [Afficher ou modifier les propriétés d'une stratégie de gestion basée sur des stratégies](view-or-modify-the-properties-of-a-policy-based-management-policy.md)|  
|Décrit comment exporter et importer une stratégie de Gestion basée sur des stratégies.|[Exporter une stratégie de gestion basée sur des stratégies](export-a-policy-based-management-policy.md)<br /><br /> [Importer une stratégie de gestion basée sur des stratégies](import-a-policy-based-management-policy.md)|  
|Décrit comment vérifier qu'une instance de serveur, une base de données, un objet serveur ou un objet de base de données est conforme à une stratégie.|[Évaluer une stratégie de gestion basée sur des stratégies à partir d'un objet](evaluate-a-policy-based-management-policy-from-an-object.md)<br /><br /> [Évaluer une stratégie de gestion basée sur des stratégies pour cette stratégie](evaluate-a-policy-based-management-policy-from-that-policy.md)<br /><br /> [Évaluer une stratégie de gestion basée sur des stratégies sur une planification](evaluate-a-policy-based-management-policy-on-a-schedule.md)|  
|Décrit comment afficher et copier un état de facette de la Gestion basée sur des stratégies vers un fichier.|[Utiliser les facettes de la gestion basée sur des stratégies](working-with-policy-based-management-facets.md)|  
|Propose un ensemble de fichiers de stratégie que vous pouvez importer en tant que stratégies de meilleures pratiques et décrit comment évaluer ces stratégies par rapport à un jeu de cibles qui inclut des instances, des objets d'instance, des bases de données ou des objets de base de données.|[Surveiller et appliquer les bonnes pratiques à l'aide de la Gestion basée sur des stratégies](monitor-and-enforce-best-practices-by-using-policy-based-management.md)|  
|Fournit les rubriques d’aide, accessibles via la touche F1, relatives au nœud **Gestion de la stratégie** de l’Explorateur d’objets dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].|[Nœud Gestion de la stratégie &#40;Explorateur d’objets&#41;](../../ssms/object/object-explorer.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de la Gestion basée sur des stratégies &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/policy-based-management-views-transact-sql)  
  
  
