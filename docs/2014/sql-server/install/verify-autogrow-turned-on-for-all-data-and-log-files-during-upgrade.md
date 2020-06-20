---
title: Vérifier que la croissance automatique est activée pour tous les fichiers de données et fichiers journaux pendant le processus de mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], size
- data files [SQL Server], size
- tempdb [SQL Server], size
- autogrow [SQL Server]
ms.assetid: a5860904-e2be-4224-8a51-df18a10d3fb9
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 8ca12075598bce210a905cbdfba89f2d879cf09b
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85065188"
---
# <a name="verify-autogrow-is-turned-on-for-all-data-and-log-files-during-the-upgrade-process"></a>Vérifier que la croissance automatique est activée pour tous les fichiers de données et fichiers journaux pendant le processus de mise à niveau
  Le Conseiller de mise à niveau a détecté des fichiers de données ou des fichiers journaux pour lesquels la croissance automatique n'est pas activée. Les fonctionnalités nouvelles et améliorées nécessitent de l’espace disque supplémentaire pour les bases de données utilisateur et la base de données système **tempdb** . Pour garantir que les ressources peuvent s’adapter aux augmentations de taille lors de la mise à niveau et aux opérations de production suivantes, nous vous recommandons de définir la croissance automatique sur activé pour tous les fichiers journaux et de données utilisateur, ainsi que les fichiers journaux et de données **tempdb** avant la mise à niveau.  
  
 Une fois que vous avez effectué la mise à niveau et testé vos charges de travail, vous pouvez désactiver la croissance automatique ou modifier l'incrément FILEGROWTH selon vos besoins en termes de fichiers de données et fichiers journaux utilisateur. Nous recommandons que la croissance automatique reste activée pour la base de données système **tempdb** . Pour plus d'informations, consultez « Planification des capacités de tempdb » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 **Fichiers de données**  
  
 Le tableau suivant répertorie les modifications apportées aux fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui entraînent une augmentation de l'espace disque nécessaire pour les fichiers de données définis par l'utilisateur.  
  
|Fonctionnalité|Modifications introduites dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|-------------|-----------------------------------------------------|  
|Texte intégral|Le plan DOCID (Document ID) est stocké dans le fichier de données et non pas dans le catalogue de texte intégral.|  
|Colonnes `text`, `ntext` et `image`|Chaque colonne LOB (Large Object) définie dans les types de données `text`, `ntext` ou `image` a besoin de 40 octets d'espace disque supplémentaire. Cette expansion ne se produit qu'une fois, durant la première mise à jour de chaque colonne LOB.|  
|metadata|Des métadonnées système supplémentaires sont créées et conservées dans le groupe de fichiers PRIMARY de chaque base de données utilisateur pour les objets de base de données et les autorisations d'utilisateurs. Par exemple, dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les autorisations associées à un fournisseur ou un bénéficiaire d'autorisations étaient stockées sur une seule ligne sous forme de bitmap. Le bitmap s'étend sur plusieurs lignes.<br /><br /> Pendant le processus de mise à niveau, il faut suffisamment d'espace disque pour stocker les métadonnées anciennes et nouvelles. Les anciennes métadonnées sont supprimées à la fin de la mise à niveau.|  
  
 **Fichiers journaux de transactions**  
  
 Le tableau suivant répertorie les modifications apportées aux fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui entraînent une augmentation de l'espace disque nécessaire pour les fichiers journaux de transactions définis par l'utilisateur.  
  
|Fonctionnalité|Modifications introduites dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|-------------|-----------------------------------------------------|  
|Restauration et récupération|Durant la phase de restauration d'une récupération après panne, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permet aux utilisateurs d'accéder à la base de données. Cela est possible parce que les transactions qui n'étaient pas validées lorsque l'incident s'est produit retrouvent les verrous dont elles disposaient avant l'incident. Si les transactions sont en cours de restauration, leurs verrous les protègent contre les interférences des utilisateurs. Ces informations de verrouillage complémentaires doivent être conservées dans le journal des transactions.|  
  
 **fichiers de données et fichiers journaux tempdb**  
  
 Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , la base de données **tempdb** est utilisée pour stocker les objets suivants :  
  
-   les objets temporaires créés explicitement, tels que les tables, les procédures stockées, les variables de table ou les curseurs ;  
  
-   les tables de travail internes créées par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ;  
  
-   les résultats de tris temporaires lorsque vous créez ou régénérez des index, si SORT_IN_TEMPDB est spécifié.  
  
 Les objets supplémentaires utilisent également la base de données **tempdb** . Le tableau suivant répertorie les modifications ou les ajouts apportés aux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctionnalités qui entraînent l’espace disque supplémentaire requis pour les fichiers journaux et de données **tempdb** .  
  
|Fonctionnalité|Modifications introduites dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|-------------|-----------------------------------------------------|  
|Contrôle de version de ligne|Le contrôle de version de ligne est un cadre général dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui permet d'effectuer les opérations suivantes :<br /><br /> Déclencheurs de prise en charge : créez les tables inserted et Deleted dans les déclencheurs. Toutes les lignes modifiées par le déclencheur reçoivent une version, y compris celles modifiées par l'instruction qui a lancé le déclencheur, de même que toute modification de données effectuée par le déclencheur. Les déclencheurs AFTER utilisent la Banque des versions de **tempdb** pour conserver les images des lignes modifiées par le déclencheur. Si les déclencheurs sont activés lors d'un chargement de données en masse, une copie de chaque ligne est ajoutée à la banque des versions.<br /><br /> Prise en charge des ensembles de résultats actifs multiples (MARS, Multiple Active Result Sets). Si une session MARS publie une instruction de modification de données (par exemple, INSERT, UPDATE ou DELETE) à un moment où il y a un ensemble de résultats actif, les lignes concernées par l'instruction de modification sont avec version.<br /><br /> Prise en charge des opérations d'index qui spécifient l'option ONLINE. Les opérations d'index en ligne utilisent le contrôle de version de ligne pour isoler l'opération d'index des effets des modifications d'autres transactions. Ceci permet d'éviter de demander des verrous partagés sur des lignes qui ont été lues. En outre, les opérations de mise à jour et de suppression des utilisateurs simultanés pendant les opérations d’index en ligne nécessitent de l’espace pour les enregistrements de version dans **tempdb**.<br /><br /> Prendre en charge les niveaux d’isolation des transactions basés sur le contrôle de version de ligne : une nouvelle implémentation du niveau d’isolation Read Committed qui utilise le contrôle de version de ligne pour assurer la cohérence de lecture au niveau de l’instruction. Un nouveau niveau d'isolement, l'instantané, pour assurer la cohérence de la lecture au niveau de la transaction.<br /><br /> <br /><br /> Les versions de ligne sont conservées dans la Banque des versions **tempdb** suffisamment longtemps pour répondre aux exigences des transactions s’exécutant sous des niveaux d’isolement basés sur le contrôle de version de ligne.<br /><br /> Pour plus d'informations sur le contrôle de version de ligne et la banque des versions, consultez la rubrique « Présentation des niveaux d'isolement basés sur le contrôle de version de ligne » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Mise en cache des métadonnées de table temporaire et de variable temporaire|Pour chaque métadonnées de la table temporaire et de la variable TEMP mises en cache dans le cache de métadonnées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , deux pages supplémentaires sont allouées pour **tempdb**.<br /><br /> Si une procédure stockée ou un déclencheur crée une table ou variable temporaire, l'objet temporaire n'est pas supprimé à la fin de l'exécution de la procédure ou du déclencheur. À la place, l'objet temporaire est tronqué en une page et réutilisé lors de la prochaine exécution de la procédure ou du déclencheur.|  
|Index sur des tables partitionnées|Lorsque le [!INCLUDE[ssDE](../../includes/ssde-md.md)] effectue un tri pour générer des index partitionnés, un espace suffisant pour contenir les exécutions de tri intermédiaires de chaque partition est requis dans **tempdb** si l’option d’index SORT_IN_TEMPDB est spécifiée.|  
|[!INCLUDE[ssSB](../../includes/sssb-md.md)]|[!INCLUDE[ssSB](../../includes/sssb-md.md)]utilise explicitement **tempdb** lors de la préservation du contexte de dialogue existant qui ne peut pas rester en mémoire (environ 1 Ko par boîte de dialogue).<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)]utilise implicitement **tempdb** via la mise en cache des objets dans le contexte de l’exécution de la requête. comme les tables de travail utilisées pour les événements de la minuterie et les conversations fournies en arrière-plan.<br /><br /> Les fonctionnalités DBMail, notifications d'événements et notifications de requêtes utilisent implicitement [!INCLUDE[ssSB](../../includes/sssb-md.md)].|  
|Type de données LOB (Large Object)<br /><br /> Variables et paramètres LOB|Les types de données `varchar(max)` , `nvarchar(max)` , **varbinary (max) Text**, `ntext` `image,` et `xml` sont des types d’objets volumineux.<br /><br /> Lorsqu’un niveau d’isolation des transactions basé sur le contrôle de version de ligne est activé sur la base de données et que les modifications des objets volumineux sont effectuées, le fragment modifié du LOB est copié dans la Banque des versions de **tempdb**.<br /><br /> Les paramètres définis en tant que type de données objet volumineux sont stockés dans **tempdb**.|  
|Expressions de table communes (CTE)|Les tables de travail temporaires pour les opérations de mise en file d’attente sont créées dans **tempdb** lorsque des requêtes d’expressions de table communes sont exécutées.|  
  
## <a name="corrective-action"></a>Action corrective  
 Pour activer la croissance automatique d'un fichier de données ou d'un fichier journal, modifiez les instructions suivantes pour spécifier les données et le journal de votre base de données. Vous devez attribuer à l'incrément FILEGROWTH une valeur adaptée à votre environnement.  
  
```  
ALTER DATABASE tempdb  
MODIFY FILE  
    (NAME = tempdev,  
    FILEGROWTH = 20MB);  
GO  
ALTER DATABASE tempdb  
MODIFY FILE  
    (NAME = templog,  
    FILEGROWTH = 10MB);  
```  
  
 L'incrément de croissance par défaut pour les fichiers de données est égal à 1 Mo. La valeur par défaut attribuée au fichier journal est égale à 10 %. Nous recommandons d'appliquer les indications suivantes lors de la définition de l'incrément FILEGROWTH :  
  
|Taille du fichier|Incrément FILEGROWTH|  
|---------------|--------------------------|  
|De 0 à 50 Mo|10 Mo|  
|De 100 à 200 Mo|20 Mo|  
|500 Mo ou plus|10 %|  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
