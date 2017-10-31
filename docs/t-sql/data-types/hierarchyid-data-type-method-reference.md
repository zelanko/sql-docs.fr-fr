---
title: hierarchyid (Transact-SQL) | Documents Microsoft
ms.custom: 
ms.date: 7/22/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- hierarchyid
- hierarchyid_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- Hierarchy data type
- hierarchyid data type
ms.assetid: 69b756e0-a1df-45b3-8a24-6ded8658aefe
caps.latest.revision: 29
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 44299e7ddb90bdd52e2638dd859993513bd6f966
ms.contentlocale: fr-fr
ms.lasthandoff: 09/01/2017

---
# <a name="hierarchyid-data-type-method-reference"></a>référence de méthode de type de données hierarchyid
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Le **hierarchyid** type de données est une longueur variable, type de données système. Utilisez **hierarchyid** pour représenter la position dans une hiérarchie. Une colonne de type **hierarchyid** ne représente pas automatiquement une arborescence. Il appartient à l'application de générer et d'assigner des valeurs **hierarchyid** de telle façon que la relation voulue entre les lignes soit reflétée dans les valeurs.
  
Une valeur du type de données **hierarchyid** représente une position dans une hiérarchie d'arborescence. Les valeurs de **hierarchyid** ont les propriétés suivantes :
  
-   Extrêmement compact  
     Le nombre moyen de bits nécessaires pour représenter un nœud dans une arborescence avec *n* nœuds dépend de la sortance moyenne (nombre moyen d’enfants d’un nœud). Pour les petites sortances (0-7), la taille est d’environ 6\*logA *n*  bits, où A est la sortance moyenne. Un nœud dans une hiérarchie d'organisation de 100 000 personnes avec une sortance moyenne de 6 niveaux prend approximativement 38 bits. Ce chiffre est arrondi à 40 bits, ou 5 octets, pour le stockage.  
-   La comparaison est effectuée dans l'ordre à profondeur prioritaire  
     Étant donné deux valeurs **hierarchyid** **a** et **b**, **a<b** signifie que a se situe avant b dans un parcours à profondeur prioritaire de l’arborescence. Les index sur les types de données **hierarchyid** sont dans l’ordre à profondeur prioritaire, et les nœuds proches les uns des autres dans un parcours à profondeur prioritaire sont stockés les uns à côté des autres. Par exemple, les enfants d'un enregistrement sont stockés à côté de cet enregistrement. Pour plus d’informations, consultez [hiérarchique de données &#40; SQL Server &#41; ](../../relational-databases/hierarchical-data-sql-server.md).  
-   Prise en charge des insertions et suppressions arbitraires  
     En utilisant la méthode [GetDescendant](../../t-sql/data-types/getdescendant-database-engine.md) , il est toujours possible de générer un frère à droite d'un nœud donné, à gauche d'un nœud donné, ou entre les deux frères. La propriété de comparaison est maintenue lorsqu'un nombre arbitraire de nœuds est inséré ou supprimé dans la hiérarchie. La plupart des insertions et suppressions préservent la propriété de compacité. Toutefois, les insertions entre deux nœuds produiront des valeurs hierarchyid avec une représentation légèrement moins compacte.  
-   L’encodage utilisé dans le **hierarchyid** type est limité à 892 octets. Par conséquent, les nœuds qui ont trop de niveaux dans leur représentation pour s’adapter à 892 octets ne peut pas être représentés par le **hierarchyid** type.  
  
Le **hierarchyid** type est disponible pour les clients CLR comme le **SqlHierarchyId** type de données.
  
## <a name="remarks"></a>Notes  
Le **hierarchyid** type encode logiquement les informations sur un seul nœud dans une arborescence hiérarchique en encodant le chemin d’accès de la racine de l’arborescence au nœud. Un tel chemin d'accès est représenté logiquement comme une séquence d'étiquettes de nœud de tous les enfants visités après la racine. Une barre oblique démarre la représentation et un chemin d'accès qui visite uniquement la racine est représenté par une barre oblique unique. Pour les niveaux sous la racine, chaque étiquette est encodée comme une séquence d'entiers séparés par des points. La comparaison entre les enfants est effectuée en comparant les séquences d'entiers séparés par des points dans le classement du dictionnaire. Chaque niveau est suivi d'une barre oblique. Par conséquent, une barre oblique sépare les parents de leurs enfants. Par exemple, les éléments suivants sont valides **hierarchyid** chemins d’accès de longueurs 1, 2, 2, 3 et 3 niveaux respectivement :
  
-   /  
  
-   /1/  
  
-   /0.3.-7/  
  
-   /1/3/  
  
-   /0.1/0.2/  
  
Les nœuds peuvent être insérés à tout emplacement. Nœuds insérés après **/1/2/** mais avant **/1/3/** peut être représenté en tant que **/1/2.5/**. Les nœuds insérés avant 0 ont comme représentation logique un nombre négatif. Par exemple, un nœud qui précède **/1/1/** peut être représenté en tant que **/1/1 /**. Les nœuds ne peuvent pas avoir de zéros non significatifs. Par exemple, **/1/1.1/** est valide, mais **/1/1.01/** n’est pas valide. Pour éviter les erreurs, insérer des nœuds à l’aide de la [GetDescendant](../../t-sql/data-types/getdescendant-database-engine.md) (méthode).
  
## <a name="data-type-conversion"></a>Conversion de type de données
Le **hierarchyid** type de données peut être converti en d’autres types de données comme suit :
-   Utilisez le [ToString()](../../t-sql/data-types/tostring-database-engine.md) méthode pour convertir le **hierarchyid** valeur comme représentation logique un **nvarchar (4000)** type de données.  
-   Utilisez [lire ()](../../t-sql/data-types/read-database-engine.md) et [Write ()](../../t-sql/data-types/write-database-engine.md) à convertir **hierarchyid** à **varbinary**.  
-   Pour transmettre **hierarchyid** paramètres via SOAP convertissez-les d’abord en tant que chaînes.  
  
## <a name="upgrading-databases"></a>La mise à niveau des bases de données
Lorsqu’une base de données est mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], le nouvel assembly et le **hierarchyid** est automatiquement installé le type de données. Les règles du Conseiller de mise à niveau détectent tout type d’utilisateur ou des assemblys avec des noms incompatibles. Le Conseiller de mise à niveau recommandera de renommer tout assembly incompatible, et de renommer tout type en conflit ou d'utiliser des noms en deux parties dans le code pour faire référence à ce type d'utilisateur préexistant.
  
Si une mise à niveau de base de données détecte un assembly utilisateur avec un nom en conflit, elle renommera automatiquement cet assembly et placera la base de données en mode suspect.
  
Si un type d'utilisateur avec un nom en conflit existe pendant la mise à niveau, aucune étape spéciale n'est suivie. Après la mise à niveau, l'ancien type d'utilisateur et le nouveau type de système existeront tous deux. Le type d'utilisateur sera disponible uniquement en utilisant des noms en deux parties.
  
## <a name="using-hierarchyid-columns-in-replicated-tables"></a>Utilisation de colonnes hierarchyid dans les tables répliquées
Colonnes de type **hierarchyid** peut être utilisé sur une table répliquée. La configuration requise pour votre application varie si la réplication est unidirectionnelle ou bidirectionnelle, et selon les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui sont utilisées.
  
### <a name="one-directional-replication"></a>Réplication unidirectionnelle
La réplication unidirectionnelle inclut les réplications d'instantanés, transactionnelle et de fusion dans laquelle les modifications ne sont pas apportées au niveau de l'abonné. Comment **hierarchyid qui** utiliser les colonnes avec une réplication unidirectionnelle dépend de la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’abonné est en cours d’exécution.
-   A [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Publisher peut répliquer **hierarchyid qui** colonnes à une [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] abonné sans considérations particulières.  
-   A [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Publisher doit convertir **hierarchyid** colonnes pour les répliquer vers un abonné qui est en cours d’exécution [!INCLUDE[ssEW](../../includes/ssew-md.md)] ou une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)]et les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne gèrent pas **hierarchyid** colonnes. Si vous utilisez l'une de ces versions, vous pouvez encore répliquer des données vers un abonné. Pour ce faire, vous devez définir une option de schéma ou le niveau de compatibilité de la publication (pour la réplication de fusion) afin que la colonne puisse être convertie en un type de données compatible.  
  
Le filtrage de colonne est pris en charge dans ces deux scénarios. Cela inclut l’exclusion des **hierarchyid** colonnes. Filtrage des lignes est prise en charge tant que le filtre n’inclut pas un **hierarchyid** colonne.
  
### <a name="bi-directional-replication"></a>Réplication bidirectionnelle
La réplication bidirectionnelle inclut la réplication transactionnelle avec mise à jour des abonnements, la réplication transactionnelle d'égal à égal et la réplication de fusion dans laquelle les modifications sont apportées au niveau de l'abonné. La réplication vous permet de configurer une table avec **hierarchyid** colonnes pour une réplication bidirectionnelle. Notez la configuration requise et les considérations suivantes :
-   Le serveur de publication et tous les abonnés doivent exécuter [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
-   La réplication réplique les données comme octets et n'effectue aucune validation pour assurer l'intégrité de la hiérarchie.  
-   La hiérarchie des modifications qui ont été apportées à la source (abonné ou serveur de publication) n'est pas conservée lorsqu'elles sont répliquées vers la destination.  
-   Les valeurs de hachage pour **hierarchyid** colonnes sont spécifiques à la base de données dans lequel ils sont générés. Par conséquent, la même valeur pourrait être générée sur le serveur de publication et l'abonné, mais pourrait être appliquée sur des lignes différentes. La réplication ne vérifie pas cette condition, et il n’existe aucune méthode intégrée pour partitionner **hierarchyid** les valeurs de colonne comme pour les colonnes d’identité. Les applications doivent utiliser des contraintes ou d'autres mécanismes pour éviter de tels conflits non détectés.  
-   Il est possible que les lignes qui sont insérées sur l'abonné soient orphelines. La ligne parente de la ligne insérée a pu être supprimée au niveau du serveur de publication. Cela provoque un conflit non détecté lorsque la ligne de l'abonné est insérée au niveau du serveur de publication.  
-   Filtres de colonnes ne peuvent pas exclure acceptant **hierarchyid** colonnes : insertions de l’abonné échoueront, car il n’existe aucune valeur par défaut pour le **hierarchyid** colonne sur le serveur de publication.  
-   Filtrage des lignes est prise en charge tant que le filtre n’inclut pas un **hierarchyid** colonne.  
  
## <a name="see-also"></a>Voir aussi
[Données hiérarchiques &#40;SQL Server&#41;](../../relational-databases/hierarchical-data-sql-server.md)  
[Référence de méthodes de type de données hierarchyid](http://msdn.microsoft.com/library/01a050f5-7580-4d5f-807c-7f11423cbb06)
  
  

