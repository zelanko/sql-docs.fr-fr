---
title: Vérifiez la croissance automatique est activée pour toutes les données et les fichiers journaux pendant le processus de mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- log files [SQL Server], size
- data files [SQL Server], size
- tempdb [SQL Server], size
- autogrow [SQL Server]
ms.assetid: a5860904-e2be-4224-8a51-df18a10d3fb9
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ab29cc94071b95f6ff8cffb95902851d1796ed80
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62985866"
---
# <a name="verify-autogrow-is-turned-on-for-all-data-and-log-files-during-the-upgrade-process"></a>Vérifier que la croissance automatique est activée pour tous les fichiers de données et fichiers journaux pendant le processus de mise à niveau
  Le Conseiller de mise à niveau a détecté des fichiers de données ou des fichiers journaux pour lesquels la croissance automatique n'est pas activée. Fonctionnalités nouvelles et améliorées nécessitent un espace disque supplémentaire pour les bases de données utilisateur et le **tempdb** base de données système. Pour vous assurer de ressources peuvent s’adapter aux augmentations de taille au cours de mise à niveau et les opérations de production suivantes, nous vous recommandons de l’option croissance automatique pour tous les fichiers de données et journaux utilisateur et le **tempdb** données et fichiers journaux avant la mise à niveau.  
  
 Une fois que vous avez effectué la mise à niveau et testé vos charges de travail, vous pouvez désactiver la croissance automatique ou modifier l'incrément FILEGROWTH selon vos besoins en termes de fichiers de données et fichiers journaux utilisateur. Nous vous recommandons de laisser la croissance automatique activée pour le **tempdb** base de données système. Pour plus d'informations, consultez « Planification des capacités de tempdb » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 **Fichiers de données**  
  
 Le tableau suivant répertorie les modifications apportées aux fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui entraînent une augmentation de l'espace disque nécessaire pour les fichiers de données définis par l'utilisateur.  
  
|Fonctionnalité|Modifications introduites dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|-------------|-----------------------------------------------------|  
|Texte intégral|Le plan DOCID (Document ID) est stocké dans le fichier de données et non pas dans le catalogue de texte intégral.|  
|Colonnes `text`, `ntext` et `image`|Chaque colonne LOB (Large Object) définie dans les types de données `text`, `ntext` ou `image` a besoin de 40 octets d'espace disque supplémentaire. Cette expansion ne se produit qu'une fois, durant la première mise à jour de chaque colonne LOB.|  
|métadonnées|Des métadonnées système supplémentaires sont créées et conservées dans le groupe de fichiers PRIMARY de chaque base de données utilisateur pour les objets de base de données et les autorisations d'utilisateurs. Par exemple, dans les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], les autorisations associées à un fournisseur ou un bénéficiaire d'autorisations étaient stockées sur une seule ligne sous forme de bitmap. Le bitmap s'étend sur plusieurs lignes.<br /><br /> Pendant le processus de mise à niveau, il faut suffisamment d'espace disque pour stocker les métadonnées anciennes et nouvelles. Les anciennes métadonnées sont supprimées à la fin de la mise à niveau.|  
  
 **Fichiers journaux des transactions**  
  
 Le tableau suivant répertorie les modifications apportées aux fonctionnalités de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui entraînent une augmentation de l'espace disque nécessaire pour les fichiers journaux de transactions définis par l'utilisateur.  
  
|Fonctionnalité|Modifications introduites dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|-------------|-----------------------------------------------------|  
|Restauration et récupération|Durant la phase de restauration d'une récupération après panne, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permet aux utilisateurs d'accéder à la base de données. Cela est possible parce que les transactions qui n'étaient pas validées lorsque l'incident s'est produit retrouvent les verrous dont elles disposaient avant l'incident. Tandis que les transactions sont en cours de restauration, leurs verrous les protègent contre les interférences par les utilisateurs. Ces informations de verrouillage complémentaires doivent être conservées dans le journal des transactions.|  
  
 **fichiers journaux et de données tempdb**  
  
 Dans les versions antérieures de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le **tempdb** base de données est utilisé pour stocker les objets suivants :  
  
-   les objets temporaires créés explicitement, tels que les tables, les procédures stockées, les variables de table ou les curseurs ;  
  
-   les tables de travail internes créées par le [!INCLUDE[ssDE](../../includes/ssde-md.md)] ;  
  
-   les résultats de tris temporaires lorsque vous créez ou régénérez des index, si SORT_IN_TEMPDB est spécifié.  
  
 Objets supplémentaires utilisent également le **tempdb** base de données. Le tableau suivant répertorie les modifications ou ajouts apportés aux [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fonctionnalités entraînent une augmentation espace disque nécessaire pour **tempdb** données et les fichiers journaux.  
  
|Fonctionnalité|Modifications introduites dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|-------------|-----------------------------------------------------|  
|Contrôle de version de ligne|Le contrôle de version de ligne est un cadre général dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui permet d'effectuer les opérations suivantes :<br /><br /> Prise en charge des déclencheurs : Créer les tables inserted et deleted dans les déclencheurs. Toutes les lignes modifiées par le déclencheur reçoivent une version, y compris celles modifiées par l'instruction qui a lancé le déclencheur, de même que toute modification de données effectuée par le déclencheur. Déclencheurs AFTER utilisent la banque des versions de **tempdb** pour stocker les images des lignes modifiées par le déclencheur. Si les déclencheurs sont activés lors d'un chargement de données en masse, une copie de chaque ligne est ajoutée à la banque des versions.<br /><br /> Prise en charge des ensembles de résultats actifs multiples (MARS, Multiple Active Result Sets). Si une session MARS publie une instruction de modification de données (par exemple, INSERT, UPDATE ou DELETE) à un moment où il y a un ensemble de résultats actif, les lignes concernées par l'instruction de modification sont avec version.<br /><br /> Prise en charge des opérations d'index qui spécifient l'option ONLINE. Les opérations d'index en ligne utilisent le contrôle de version de ligne pour isoler l'opération d'index des effets des modifications d'autres transactions. Ceci permet d'éviter de demander des verrous partagés sur des lignes qui ont été lues. En outre, les utilisateurs simultanés mettre à jour et les opérations de suppression lors de l’index en ligne opérations nécessitent un espace pour les enregistrements de version dans **tempdb**.<br /><br /> Prise en charge des niveaux d'isolement des transactions basés sur le contrôle de version de ligne : Une nouvelle implémentation du niveau d'isolement read committed qui utilise le contrôle de version de ligne pour assurer la cohérence de la lecture au niveau de l'instruction. Un nouveau niveau d'isolement, l'instantané, pour assurer la cohérence de la lecture au niveau de la transaction.<br /><br /> <br /><br /> Les versions de ligne sont conservées dans le **tempdb** la banque des versions depuis suffisamment longtemps pour satisfaire les exigences de transactions qui s’exécutent sous des niveaux d’isolement basé sur le contrôle de version de ligne.<br /><br /> Pour plus d'informations sur le contrôle de version de ligne et la banque des versions, consultez la rubrique « Présentation des niveaux d'isolement basés sur le contrôle de version de ligne » dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Mise en cache des métadonnées de table temporaire et de variable temporaire|Pour chaque métadonnée de table temporaire et variable temporaire placée dans le cache de métadonnées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], deux pages supplémentaires sont allouées pour **tempdb**.<br /><br /> Si une procédure stockée ou un déclencheur crée une table ou variable temporaire, l'objet temporaire n'est pas supprimé à la fin de l'exécution de la procédure ou du déclencheur. À la place, l'objet temporaire est tronqué en une page et réutilisé lors de la prochaine exécution de la procédure ou du déclencheur.|  
|Index sur des tables partitionnées|Lorsque le [!INCLUDE[ssDE](../../includes/ssde-md.md)] effectue un tri pour générer des index partitionnés, suffisamment d’espace pour contenir les tris intermédiaires de chaque partition est requis dans **tempdb** si l’option d’index SORT_IN_TEMPDB est spécifiée.|  
|[!INCLUDE[ssSB](../../includes/sssb-md.md)]|[!INCLUDE[ssSB](../../includes/sssb-md.md)] utilise explicitement **tempdb** pour préserver le contexte de dialogue existant qui ne peut pas rester en mémoire (approximativement 1 Ko par dialogue).<br /><br /> [!INCLUDE[ssSB](../../includes/sssb-md.md)] utilise implicitement **tempdb** via la mise en cache d’objets dans le contexte d’exécution de la requête. comme les tables de travail utilisées pour les événements de la minuterie et les conversations fournies en arrière-plan.<br /><br /> Les fonctionnalités DBMail, notifications d'événements et notifications de requêtes utilisent implicitement [!INCLUDE[ssSB](../../includes/sssb-md.md)].|  
|Type de données LOB (Large Object)<br /><br /> Variables et paramètres LOB|Les types de données `varchar(max)`, `nvarchar(max)`, **varbinary (max) texte**, `ntext`, `image,` et `xml` sont des types d’objets volumineux.<br /><br /> Lorsqu’un niveau d’isolement de transaction basé sur le contrôle de version de ligne est activé sur la base de données et des modifications des objets volumineux sont effectuées, le fragment modifié du LOB est copié vers la banque des versions dans **tempdb**.<br /><br /> Paramètres définis sous la forme d’un type de données d’objets volumineux sont stockés dans **tempdb**.|  
|Expressions de table communes (CTE)|Tables de travail temporaires pour les opérations de spoule sont créées dans **tempdb** lorsque les requêtes d’expressions de table communes sont exécutées.|  
  
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
|De 100 à 200 Mo|20 MO|  
|500 Mo ou plus|10%|  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
