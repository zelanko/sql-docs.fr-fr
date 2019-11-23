---
title: SQL Server de fichiers de données dans Azure | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: 38ffd9c2-18a5-43d2-b674-e425addec4e4
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 93a39c50ea81be98e723101d1d1dc076d5569171
ms.sourcegitcommit: f912c101d2939084c4ea2e9881eb98e1afa29dad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72797721"
---
# <a name="sql-server-data-files-in-azure"></a>Fichiers de données SQL Server dans Azure
  SQL Server fichiers de données dans Azure permet la prise en charge native des fichiers de base de données SQL Server stockés en tant qu’objets BLOB Azure. Elle vous permet de créer une base de données dans SQL Server s’exécutant localement ou dans une machine virtuelle dans Azure avec un emplacement de stockage dédié pour vos données dans le stockage d’objets BLOB Azure. Cette amélioration simplifie en particulier le déplacement des bases de données entre les ordinateurs, grâce aux opérations par attachement et détachement. En outre, il fournit un autre emplacement de stockage pour vos fichiers de sauvegarde de base de données en vous permettant de restaurer à partir de ou vers le stockage Azure. Par conséquent, elle permet plusieurs solutions hybrides en offrant différents avantages en matière de virtualisation des données, de déplacement des données, de sécurité et de disponibilité, le tout à des coûts et une maintenance réduits pour une mise à l'échelle élastique et une haute disponibilité.  
  
 Cette rubrique présente les concepts et les considérations essentiels au stockage des fichiers de données SQL Server dans le service de stockage Azure.  
  
 Pour une expérience pratique de l’utilisation de cette nouvelle fonctionnalité, consultez [Didacticiel : SQL Server de fichiers de données dans le service de stockage Azure](../tutorial-use-azure-blob-storage-service-with-sql-server-2016.md).  
  
 Le diagramme suivant montre que cette amélioration vous permet de stocker des fichiers de base de données SQL Server en tant qu’objets BLOB Azure dans le stockage Azure, quel que soit l’emplacement de votre serveur.  
  
 ![Intégration de SQL Server à Azure Storage](../../database-engine/media/sql-server-dbfiles-stored-as-blobs.gif "Intégration de SQL Server à Azure Storage")  
  
## <a name="benefits-of-using-sql-server-data-files-in-azure"></a>Avantages de l’utilisation des fichiers de données SQL Server dans Azure  
  
-   **Migration facile et rapide :** cette fonctionnalité simplifie le processus de migration en déplaçant une base de données à la fois entre les ordinateurs locaux ainsi qu’entre les environnements locaux et le cloud, sans aucune modification de l’application. Par conséquent, elle prend en charge une migration incrémentielle tout en conservant l'infrastructure locale existante. En outre, avoir accès à un stockage de données centralisé simplifie la logique d'application lorsqu'une application doit s'exécuter à plusieurs emplacements dans un environnement local. Dans certains cas, vous devez configurer rapidement des centres de calcul situés dans des emplacements géographiquement dispersés, qui rassemblent des données de nombreuses sources différentes. En utilisant cette nouvelle amélioration, au lieu de déplacer les données d’un emplacement à un autre, vous pouvez stocker de nombreuses bases de données en tant qu’objets BLOB Azure, puis exécuter des scripts Transact-SQL pour créer des bases de données sur les ordinateurs locaux ou les machines virtuelles.  
  
-   **Coûts et avantages de stockage illimités :** Cette fonctionnalité vous permet de disposer d’un stockage hors site illimité dans Azure tout en tirant parti des ressources de calcul locales. Lorsque vous utilisez Azure comme emplacement de stockage, vous pouvez facilement vous concentrer sur la logique d’application sans la surcharge de la gestion du matériel. Si vous perdez un nœud de calcul local, vous pouvez en configurer un autre sans aucun déplacement des données.  
  
-   **Avantages de la haute disponibilité et de la récupération d’urgence :** L’utilisation de SQL Server fichiers de données dans Azure peut simplifier les solutions de haute disponibilité et de récupération d’urgence. Par exemple, si une machine virtuelle dans Azure ou une instance de SQL Server se bloque, vous pouvez recréer vos bases de données dans un nouvel ordinateur en rétablissant simplement les liens vers les objets BLOB Azure.  
  
-   **Sécurité :** cette nouvelle amélioration vous permet de séparer une instance de calcul d'une instance de stockage. Vous pouvez avoir une base de données entièrement chiffrée où le déchiffrement ne concerne que l'instance de calcul, mais pas l'instance de stockage. En d'autres termes, cette nouvelle amélioration vous permet de chiffrer toutes les données dans un cloud public à l'aide de certificats TDE (Transparent Data Encryption), lesquels sont physiquement séparés des données. Les clés TDE peuvent être stockées dans la base de données master, qui est stockée localement sur votre ordinateur physiquement sécurisé et sauvegardée localement. Vous pouvez utiliser ces clés locales pour chiffrer les données, qui résident dans le stockage Azure. Si les informations d'identification du compte de stockage en nuage (cloud) sont dérobées, vos données restent sécurisées dans la mesure où les certificats TDE résident toujours localement.  
  
## <a name="concepts-and-requirements"></a>Concepts et configuration requise  
  
### <a name="azure-storage-concepts"></a>Concepts liés au stockage Azure  
 Lorsque vous utilisez la fonctionnalité Fichiers de données SQL Server dans Azure, vous devez créer un compte de stockage et un conteneur dans Azure. Ensuite, vous devez créer des informations d'identification SQL Server, qui comportent des informations sur la stratégie du conteneur ainsi qu'une signature d'accès partagé qui est nécessaire pour accéder au conteneur.  
  
 Dans Azure, un compte de stockage représente le niveau le plus élevé de l’espace de noms pour l’accès aux objets BLOB. Un compte de stockage peut contenir un nombre illimité de conteneurs, tant que leur taille totale ne dépasse pas 500 To. Pour les informations les plus récentes sur les limites de stockage, consultez [Abonnement Azure et limites, quotas et contraintes du service](https://azure.microsoft.com/documentation/articles/azure-subscription-service-limits/). Un conteneur regroupe un ensemble d'objets blob. Tous les objets blob doivent figurer dans un conteneur. Un compte peut contenir un nombre illimité de conteneurs. De la même manière, un conteneur peut également stocker un nombre illimité d'objets blob. Il existe deux types d’objets blob qui peuvent être enregistrés dans un stockage Azure : les objets blob de blocs et les objets blob de pages. Cette nouvelle fonctionnalité utilise des objets blob de pages, dont la taille peut atteindre jusqu'à 1 To, et qui sont plus efficaces lorsque les plages d'octets d'un fichier sont modifiées fréquemment. Vous pouvez accéder aux objets blob avec le format d'URL suivant : `http://storageaccount.blob.core.windows.net/<container>/<blob>`.  
  
### <a name="azure-billing-considerations"></a>Considérations sur la facturation Azure  
 L’estimation du coût d’utilisation des services Azure est une question importante dans le processus de prise de décision et de planification. Lorsque vous stockez des fichiers de données SQL Server dans le stockage Azure, vous devez payer les coûts associés au stockage et aux transactions. En outre, l’implémentation de la fonctionnalité Fichiers de données SQL Server dans le stockage Azure nécessite un renouvellement implicite du bail d’objets blob toutes les 45 à 60 secondes. Cela entraîne également des coûts de transaction par fichier de base de données (.mdf ou .ldf, par exemple). Selon nos évaluations, le coût de renouvellement des baux pour deux fichiers de base de données (.mdf et .ldf) se monte à environ 2 cents par mois d'après la grille de tarification actuelle. Nous vous recommandons de consulter les informations de la page [Azure Pricing](https://azure.microsoft.com/pricing/) (Tarifs d’Azure) pour vous aider à estimer les coûts mensuels associés à l’utilisation du stockage Azure et des machines virtuelles Azure.  
  
### <a name="sql-server-concepts"></a>Concepts de serveur SQL  
 Si vous utilisez cette nouvelle amélioration, assurez-vous de procéder comme suit :  
  
-   Créez une stratégie sur un conteneur et générez également une clé de signature d'accès partagé (SAS).  
  
-   Pour chaque conteneur utilisé par un fichier de données ou un fichier journal, créez des informations d'identification SQL Server dont le nom correspond au chemin d'accès du conteneur.  
  
-   Stockez les informations relatives au conteneur de stockage Azure, le nom de stratégie associé et la clé SAS dans la banque d’informations d’identification de SQL Server.  
  
 L’exemple suivant suppose qu’un conteneur de stockage Azure a été créé et qu’une stratégie a été créée avec des droits de lecture, d’écriture et de liste. La création d'une stratégie sur un conteneur génère une clé SAS qui peut rester non chiffrée en mémoire et qui est requise par SQL Server pour accéder aux fichiers d'objet blob dans le conteneur. Dans l'extrait de code suivant, remplacez `'your SAS key'` par une entrée similaire à la suivante : `'sr=c&si=<MYPOLICYNAME>&sig=<THESHAREDACCESSSIGNATURE>'`. Pour plus d’informations, consultez [créer et utiliser une signature d’accès partagé](https://msdn.microsoft.com/library/azure/jj721951.aspx)  
  
```sql
-- Create a credential  
CREATE CREDENTIAL [https://testdb.blob.core.windows.net/data]  
WITH IDENTITY='SHARED ACCESS SIGNATURE',  
SECRET = 'your SAS key'  
  
-- Create database with data and log files in Azure container.  
CREATE DATABASE testdb   
ON  
( NAME = testdb_dat,  
    FILENAME = 'https://testdb.blob.core.windows.net/data/TestData.mdf' )  
 LOG ON  
( NAME = testdb_log,  
    FILENAME =  'https://testdb.blob.core.windows.net/data/TestLog.ldf')
```  
  
> [!IMPORTANT]
> s’il existe des références actives aux fichiers de données dans un conteneur, toutes les tentatives de suppression des informations d’identification SQL Server correspondantes échouent.  
  
### <a name="security"></a>Sécurité  
 Vous trouverez ci-dessous les considérations de sécurité et la configuration requise pour le stockage de fichiers de données SQL Server dans le stockage Azure.  
  
-   Lorsque vous créez un conteneur pour le service de stockage d’objets blob Azure, nous vous recommandons de définir l’accès sur Privé. Lorsque vous définissez l’accès privé, le conteneur et les données blob ne peuvent être lus que par le propriétaire du compte Azure.  
  
-   Lors de l’enregistrement des fichiers de base de données SQL Server dans le stockage Azure, vous devez utiliser une signature d’accès partagé, un URI qui octroie des droits d’accès restreints aux conteneurs, aux objets blob, aux files d’attente et aux tables. À l’aide d’une signature d’accès partagé, vous pouvez autoriser SQL Server à accéder aux ressources dans votre compte de stockage sans partager votre clé de compte de stockage Azure.  
  
-   De plus, nous vous recommandons de continuer de suivre les pratiques de sécurité locales habituelles pour vos bases de données.  
  
### <a name="installation-prerequisites"></a>Conditions préalables d'installation  
 Vous trouverez ci-dessous les conditions préalables à l’installation lors du stockage SQL Server fichiers de données dans Azure.  
  
-   **SQL Server local :** SQL Server 2014 comprend cette fonctionnalité. Pour savoir comment télécharger SQL Server 2014, consultez [SQL Server 2014](https://www.microsoft.com/sqlserver/sql-server-2014.aspx).  
  
-   SQL Server s'exécutant sur un ordinateur virtuel Azure : si vous installez SQL Server sur un ordinateur virtuel Azure, installez SQL Server 2014 ou mettez à jour votre instance existante. De même, vous pouvez également créer une machine virtuelle dans Azure à l’aide d’SQL Server image de plateforme 2014. Pour savoir comment télécharger SQL Server 2014, consultez [SQL Server 2014](https://www.microsoft.com/sqlserver/sql-server-2014.aspx).  
  
###  <a name="bkmk_Limitations"></a> Limitations  
  
-   Dans la version actuelle de cette fonctionnalité, le stockage d' `FileStream` données dans le stockage Azure n’est pas pris en charge. Vous pouvez stocker des `Filestream` données dans une base de données locale intégrée au stockage Azure, mais vous ne pouvez pas déplacer les données FILESTREAM entre les machines à l’aide du stockage Azure. Pour les données `FileStream`, nous vous recommandons de continuer à utiliser les méthodes traditionnelles pour déplacer des fichiers (.mdf, .ldf) associés à Filestream entre différents ordinateurs.  
  
-   Actuellement, cette nouvelle amélioration ne prend pas en charge l’accès simultané de plusieurs instances SQL Server aux mêmes fichiers de base de données dans le Stockage Azure. Si ServerA est en ligne avec un fichier de base de données actif et si ServeurB est démarré par erreur et qu’il comporte également une base de données qui pointe vers le même fichier de données, le deuxième serveur ne parvient pas à démarrer la base de données avec un code d’erreur **5120 impossible d’ouvrir le fichier physique "%.\*ls». Erreur% d du système d’exploitation : « % ls »** .  
  
-   Seuls les fichiers .mdf, .ldf et .ndf peuvent être enregistrés dans le Stockage Azure à l’aide de la fonctionnalité Fichiers de données SQL Server dans Azure.  
  
-   En cas d’utilisation de la fonctionnalité Fichiers de données SQL Server dans Azure, la géoréplication de votre compte de stockage n’est pas prise en charge. Si un compte de stockage est géorépliqué et qu'un géobasculement a lieu, la base de données risque d'être endommagée.  
  
-   La taille d'un objet blob peut atteindre 1 To au maximum. Cette limite supérieure s’applique à chaque fichier journal ou fichier de données de base de données pouvant être enregistré dans le stockage Azure.  
  
-   Il est impossible d’enregistrer des données de l’OLTP en mémoire dans un objet blob Azure à l’aide de la fonctionnalité Fichiers de données SQL Server dans le stockage Azure. En effet, l’OLTP en mémoire dépend de `FileStream` et, dans la version actuelle de cette fonctionnalité, le stockage d' `FileStream` données dans le stockage Azure n’est pas pris en charge.  
  
-   Lors de l’utilisation de SQL Server fichiers de données dans la fonctionnalité Azure, SQL Server effectue toutes les comparaisons de chemin d’accès d’URL ou de fichier à l’aide du classement défini dans la base de données `master`.  
  
-   Les `AlwaysOn Availability Groups` sont pris en charge tant que vous n'ajoutez pas de nouveaux fichiers de base de données à la base de données primaire. Si une opération de base de données nécessite la création d'un nouveau fichier dans la base de données primaire, désactivez d'abord les groupes de disponibilité AlwaysOn dans le nœud secondaire. Puis, effectuez l'opération de base de données dans la base de données primaire et sauvegardez la base de données dans le nœud principal. Ensuite, restaurez la base de données sur le nœud secondaire, puis activez les groupes de disponibilité AlwaysOn dans le nœud secondaire. Notez que les instances de cluster de basculement AlwaysOn ne sont pas prises en charge lors de l’utilisation de la fonctionnalité fichiers de données SQL Server dans Azure.  
  
-   En mode de fonctionnement normal, SQL Server utilise des baux temporaires pour réserver des objets blob pour le stockage, avec un renouvellement du bail de chaque objet blob toutes les 45 à 60 secondes. En cas de défaillance d'un serveur et du démarrage d'une autre instance de SQL Server configurée pour utiliser les mêmes objets blob, la nouvelle instance attend jusqu'à 60 secondes, le temps que le bail existant sur l'objet blob expire. Si vous voulez attacher la base de données à une autre instance et que vous ne pouvez pas attendre l'expiration du bail pendant 60 secondes, vous pouvez résilier explicitement le bail sur l'objet blob afin d'éviter les erreurs dans les opérations d'attachement.  
  
## <a name="tools-and-programming-reference-support"></a>Prise en charge des bibliothèques de référence de programmation et des outils  
 Cette section décrit les bibliothèques de référence de programmation et les outils qui peuvent être utilisés lors du stockage de fichiers de données SQL Server dans le stockage Azure.  
  
### <a name="powershell-support"></a>Prise en charge de PowerShell  
 Dans SQL Server 2014, vous pouvez utiliser des applets de commande PowerShell pour stocker des fichiers de données SQL Server dans le service de stockage d’objets BLOB Azure en référençant un chemin d’URL de stockage d’objets BLOB au lieu d’un chemin d’accès de fichier. Vous pouvez accéder aux objets blob avec le format d'URL suivant :`: http://storageaccount.blob.core.windows.net/<container>/<blob>` .  
  
### <a name="sql-server-object-and-performance-counters-support"></a>Prise en charge des compteurs de performances et des objets SQL Server  
 Depuis SQL Server 2014, un nouvel objet SQL Server a été ajouté pour être utilisé avec la fonctionnalité Fichiers de données SQL Server dans le stockage Azure. Le nouvel objet SQL Server est appelé [SQL Server, HTTP_STORAGE_OBJECT](../performance-monitor/sql-server-http-storage-object.md) et il peut être utilisé par le Moniteur système pour surveiller l’activité lors de l’exécution de SQL Server avec le Stockage Azure.  
  
### <a name="sql-server-management-studio-support"></a>Prise en charge de SQL Server Management Studio  
 SQL Server Management Studio vous permet d'utiliser cette fonctionnalité via plusieurs fenêtres de dialogue. Par exemple, vous pouvez taper le chemin d'accès de l'URL du conteneur de stockage, tel que `https://teststorageaccnt.blob.core.windows.net/testcontainer/` sous la forme d'un **Chemin d'accès** dans plusieurs fenêtres de dialogue, telles que **Nouvelle base de données**, **Attacher la base de données**ou **Restaurer la base de données**. Pour plus d’informations, consultez [Didacticiel : SQL Server de fichiers de données dans le service de stockage Azure](../tutorial-use-azure-blob-storage-service-with-sql-server-2016.md).  
  
### <a name="sql-server-management-objects-support"></a>Prise en charge d'objets SMO (SQL Server Management Objects)  
 Quand vous utilisez la fonctionnalité Fichiers de données SQL Server dans Azure, tous les objets SMO (SQL Server Management Objects) sont pris en charge. Si un objet SMO nécessite un chemin d'accès de fichier, utilisez le format d'URL BLOB à la place d'un chemin d'accès de fichier local, tel que `https://teststorageaccnt.blob.core.windows.net/testcontainer/`. Pour plus d’informations sur les objets SMO, consultez [Guide de programmation SMO &#40;SQL Server Management Objects&#41;](../server-management-objects-smo/sql-server-management-objects-smo-programming-guide.md) dans la documentation en ligne de SQL Server.  
  
### <a name="transact-sql-support"></a>Prise en charge de Transact-SQL  
 Cette nouvelle fonctionnalité a apporté le changement suivant dans la surface d'exposition de Transact-SQL :  
  
-   Une nouvelle colonne **int** , **credential_id**, dans la vue système **sys.master_files** . La colonne **credential_id** permet aux fichiers de données prenant en charge Azure Storage d’être référencés dans sys.credentials concernant les informations d’identification créées à leur intention. Vous pouvez l'utiliser pour le dépannage, par exemple dans le cas où des informations d'identification ne peuvent pas être supprimées parce qu'elles sont utilisées par un fichier de base de données.  
  
##  <a name="bkmk_Troubleshooting"></a>Résolution des problèmes liés aux fichiers de données SQL Server dans Azure  
 Pour éviter des erreurs attribuables à des limitations ou à des fonctionnalités non prises en charge, passez d'abord en revue [Limitations](sql-server-data-files-in-microsoft-azure.md#bkmk_Limitations).  
  
 Voici la liste des erreurs possibles lorsque vous utilisez la fonctionnalité Fichiers de données SQL Server dans le stockage Azure.  
  
 **Erreurs d'authentification**  
  
-   *Impossible de supprimer les informations d’identification « %.\*ls » parce qu’elles sont utilisées par un fichier de base de données actif.*    
    Résolution : vous pouvez voir cette erreur lorsque vous tentez de supprimer des informations d’identification encore utilisées par un fichier de base de données actif dans le stockage Azure. Pour supprimer les informations d'identification, vous devez d'abord supprimer l'objet blob associé qui comporte ce fichier de base de données. Pour supprimer un objet blob dont le bail est actif, vous devez d'abord résilier le bail.  
  
-   *La signature d'accès partagé n'a pas été créée correctement sur le conteneur.*    
     Résolution : vérifiez que vous avez créé correctement une signature d'accès partagé sur le conteneur. Passez en revue les instructions fournies dans la leçon 2 du [Didacticiel : SQL Server fichiers de données dans le service de stockage Azure](../tutorial-use-azure-blob-storage-service-with-sql-server-2016.md).  
  
-   *Les informations d'identification de SQL Server n'ont pas été créées correctement.*    
    Résolution : vérifiez que vous avez utilisé une « signature d'accès partagé » pour le champ **Identité** et que vous avez créé un secret correctement. Passez en revue les instructions fournies à la leçon 3 dans [Didacticiel : SQL Server fichiers de données dans le service de stockage Azure](../tutorial-use-azure-blob-storage-service-with-sql-server-2016.md).  
  
 **Erreurs de bail d'un objet blob :**  
  
-   Erreur lors de la tentative de démarrage de SQL Server après la défaillance d'une autre instance utilisant les mêmes fichiers d'objets blob. Résolution : en mode de fonctionnement normal, SQL Server utilise des baux temporaires pour réserver des objets blob pour le stockage, avec un renouvellement du bail de chaque objet blob toutes les 45 à 60 secondes. En cas de défaillance d'un serveur et du démarrage d'une autre instance de SQL Server configurée pour utiliser les mêmes objets blob, la nouvelle instance attend jusqu'à 60 secondes, le temps que le bail existant sur l'objet blob expire. Si vous voulez attacher la base de données à une autre instance et que vous ne pouvez pas attendre l'expiration du bail pendant 60 secondes, vous pouvez résilier explicitement le bail sur l'objet blob afin d'éviter les erreurs dans les opérations d'attachement.  
  
 **Erreurs de base de données**  
  
1.  *Erreurs lors de la création d'une base de données*   
    Résolution : passez en revue les instructions fournies dans la leçon 4 du [Didacticiel : SQL Server des fichiers de données dans le service de stockage Azure](../tutorial-use-azure-blob-storage-service-with-sql-server-2016.md).  
  
2.  *Erreurs lors de l'exécution de l'instruction Alter*   
    Résolution : veillez à exécuter l'instruction Alter Database lorsque la base de données est en ligne. Lors de la copie des fichiers de données vers le stockage Azure, créez toujours un objet blob de pages, et non un objet blob de blocs. Sinon, la modification de la base de données avec l'instruction ALTER échouera. Passez en revue les instructions fournies dans la leçon 7 du [Didacticiel : SQL Server fichiers de données dans le service de stockage Azure](../tutorial-use-azure-blob-storage-service-with-sql-server-2016.md).  
  
3.  *Code d’erreur 5120 Impossible d’ouvrir le fichier physique « %.\*ls ». Erreur %d du système d’exploitation : « %ls »*    
    Résolution : actuellement, cette nouvelle amélioration ne prend pas en charge plusieurs instances de SQL Server qui accèdent en même temps aux mêmes fichiers de base de données dans le stockage Azure. Si ServerA est en ligne avec un fichier de base de données actif et si ServeurB est démarré par erreur et qu’il comporte également une base de données qui pointe vers le même fichier de données, le deuxième serveur ne parvient pas à démarrer la base de données avec un code d’erreur *5120 impossible d’ouvrir le fichier physique "%.\*ls». Erreur% d du système d’exploitation : « % ls »* .  
  
     Pour résoudre ce problème, déterminez d’abord si vous avez besoin du serveur A pour accéder au fichier de base de données dans le stockage Azure. Si vous n’en avez pas besoin, supprimez simplement toute connexion entre le serveur A et les fichiers de base de données dans le stockage Azure. Pour cela, procédez comme suit :  
  
    1.  Définissez le chemin d'accès du serveur A sur un dossier local à l'aide de l'instruction ALTER Database.  
  
    2.  Mettez la base de données hors connexion sur le serveur A.  
  
    3.  Puis, copiez les fichiers de base de données du stockage Azure dans le dossier local du serveur A. Cela garantit que le serveur A dispose toujours d’une copie de la base de données localement.  
  
    4.  Mettez la base de données en ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : SQL Server de fichiers de données dans le service de stockage Azure](../tutorial-use-azure-blob-storage-service-with-sql-server-2016.md)  
