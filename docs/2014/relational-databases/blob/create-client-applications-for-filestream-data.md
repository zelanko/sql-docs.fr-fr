---
title: Créer des applications clientes pour les données FILESTREAM | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FILESTREAM [SQL Server], Win32
ms.assetid: 8a02aff6-e54c-40c6-a066-2083e9b090aa
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 77f7144231bda8be36334513584df16cf9c0e22b
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66010180"
---
# <a name="create-client-applications-for-filestream-data"></a>Créer des applications clientes pour les données FILESTREAM
  Vous pouvez utiliser Win32 pour lire et écrire des données dans un objet BLOB FILESTREAM. Les étapes suivantes sont nécessaires :  
  
-   Lecture du chemin d'accès au fichier FILESTREAM.  
  
-   Lecture du contexte de transaction actuel.  
  
-   Obtention d'un descripteur Win32 et utilisation de celui-ci pour lire et écrire des données dans l'objet BLOB FILESTREAM.  
  
> [!NOTE]  
>  Les exemples de cette rubrique nécessitent la base de données compatible FILESTREAM et la table qui sont créées dans [Créer une base de données compatible FILESTREAM](create-a-filestream-enabled-database.md) et [Créer une table pour le stockage de données FILESTREAM](create-a-table-for-storing-filestream-data.md).  
  
##  <a name="func"></a> Fonctions permettant d'utiliser les données FILESTREAM  
 Lorsque vous utilisez FILESTREAM pour stocker des données d'objet blob, vous pouvez utiliser des API Win32 pour travailler avec les fichiers. Pour prendre en charge l'utilisation de données d'objet blob FILESTREAM dans les applications Win32, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournit les fonctions et API suivantes :  
  
-   [PathName](/sql/relational-databases/system-functions/pathname-transact-sql) retourne un chemin d'accès en tant que jeton à un objet blob. Une application utilise ce jeton pour obtenir un descripteur Win32 et traiter des données BLOB.  
  
     Lorsque la base de données qui contient des données FILESTREAM appartient à un groupe de disponibilité AlwaysOn, la fonction de chemin d'accès retourne un nom de réseau virtuel (VNN) au lieu d'un nom d'ordinateur.  
  
-   [GET_FILESTREAM_TRANSACTION_CONTEXT ()](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql) retourne un jeton qui représente la transaction actuelle d’une session. Une application utilise ce jeton pour lier des opérations de diffusion en continu de système de fichiers FILESTREAM à la transaction.  
  
-   L' [API OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) obtient un descripteur de fichier Win32. L’application utilise le descripteur pour diffuser les données FILESTREAM et peut ensuite le passer aux API Win32 suivantes : [ReadFile](https://go.microsoft.com/fwlink/?LinkId=86422), [WriteFile](https://go.microsoft.com/fwlink/?LinkId=86423), [TransmitFile](https://go.microsoft.com/fwlink/?LinkId=86424), [SetFilePointer](https://go.microsoft.com/fwlink/?LinkId=86425), [SetEndOfFile](https://go.microsoft.com/fwlink/?LinkId=86426), ou [FlushFileBuffers](https://go.microsoft.com/fwlink/?LinkId=86427). Si l'application appelle toute autre API en utilisant le descripteur, une erreur ERROR_ACCESS_DENIED est retournée. L'application doit fermer le descripteur à l'aide de [CloseHandle](https://go.microsoft.com/fwlink/?LinkId=86428).  
  
 Tout accès au conteneur de données FILESTREAM est exécuté dans une transaction [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . [!INCLUDE[tsql](../../includes/tsql-md.md)] peuvent être exécutées dans la même transaction afin de maintenir la cohérence entre les données SQL et les données FILESTREAM.  
  
##  <a name="steps"></a> Étapes à suivre pour accéder aux données FILESTREAM  
  
###  <a name="path"></a> Lecture du chemin d'accès au fichier FILESTREAM  
 Chaque cellule d'une table FILESTREAM est associée à un chemin d'accès au fichier. Pour lire le chemin d'accès, utilisez la propriété `PathName` d'une colonne `varbinary(max)` dans une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)]. L'exemple suivant montre comment lire le chemin d'accès d'une colonne `varbinary(max)`.  
  
 [!code-sql[FILESTREAM#FS_PathName](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_pathname)]  
  
###  <a name="trx"></a> Lecture du contexte de transaction  
 Pour obtenir le contexte de transaction actuel, utilisez la fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] [GET_FILESTREAM_TRANSACTION_CONTEXT()](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql) . L'exemple suivant montre comment commencer une transaction et lire le contexte de transaction actuel.  
  
 [!code-sql[FILESTREAM#FS_GET_TRANSACTION_CONTEXT](../../snippets/tsql/SQL15/tsql/filestream/transact-sql/filestream.sql#fs_get_transaction_context)]  
  
###  <a name="handle"></a> Obtention d'un descripteur de fichier Win32  
 Pour obtenir un descripteur de fichier Win32, appelez l’API OpenSqlFilestream. Cette API est exportée à partir du fichier sqlncli.dll. Le descripteur renvoyé peut être passé à chacune des API Win32 suivantes : [ReadFile](https://go.microsoft.com/fwlink/?LinkId=86422), [WriteFile](https://go.microsoft.com/fwlink/?LinkId=86423), [TransmitFile](https://go.microsoft.com/fwlink/?LinkId=86424), [SetFilePointer](https://go.microsoft.com/fwlink/?LinkId=86425), [SetEndOfFile](https://go.microsoft.com/fwlink/?LinkId=86426), ou [FlushFileBuffers](https://go.microsoft.com/fwlink/?LinkId=86427). Les exemples suivants montrent comment obtenir un descripteur de fichier Win32 et l'utiliser pour lire et écrire des données dans un BLOB FILESTREAM.  
  
 [!code-csharp[FILESTREAM#FS_CS_ReadAndWriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/cs/filestream.cs#fs_cs_readandwriteblob)]  
  
 [!code-vb[FILESTREAM#FS_VB_ReadAndWriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/vb/filestream.vb#fs_vb_readandwriteblob)]  
  
 [!code-cpp[FILESTREAM#FS_CPP_WriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/cpp/filestream.cpp#fs_cpp_writeblob)]  
  
##  <a name="best"></a> Meilleures pratiques pour la conception et l'implémentation d'applications  
  
-   Lorsque vous concevez et implémentez des applications qui utilisent FILESTREAM, prenez en compte les recommandations suivantes :  
  
-   Utilisez NULL au lieu de 0x pour représenter une colonne FILESTREAM non initialisée. La valeur 0x entraîne la création d'un fichier, contrairement à la valeur NULL.  
  
-   Évitez les opérations d'insertion et de suppression dans les tables qui contiennent des colonnes FILESTREAM non Null. Les opérations d'insertion et de suppression peuvent modifier les tables FILESTREAM utilisées pour le garbage collection. Cela peut provoquer une dégradation des performances d'une application dans le temps.  
  
-   Dans les applications qui ont recours à la réplication, utilisez NEWSEQUENTIALID() au lieu de NEWID(). NEWSEQUENTIALID() est plus performant que NEWID() pour la génération de GUID dans ces applications.  
  
-   L'API FILESTREAM est conçue pour l'accès en continu Win32 aux données. Évitez d’utiliser [!INCLUDE[tsql](../../includes/tsql-md.md)] pour lire ou écrire des objets blob FILESTREAM de plus de 2 Mo. Si vous devez lire ou écrire des données BLOB à l'aide de [!INCLUDE[tsql](../../includes/tsql-md.md)], assurez-vous que toutes les données BLOB sont consommées avant d'essayer d'ouvrir l'objet blob FILESTREAM à partir de Win32. Si toutes les données [!INCLUDE[tsql](../../includes/tsql-md.md)] ne sont pas consommées, cela peut provoquer l'échec des opérations FILESTREAM d'ouverture ou de fermeture successives.  
  
-   Évitez les instructions [!INCLUDE[tsql](../../includes/tsql-md.md)] qui permettent de mettre à jour ou d'ajouter des données à l'objet BLOB FILESTREAM. En effet, les données BLOB sont mises en file d'attente dans la base de données tempdb, puis retournées dans un nouveau fichier physique.  
  
-   Évitez d'ajouter de petites mises à jour BLOB à un objet BLOB FILESTREAM. Chaque ajout entraîne la copie des fichiers FILESTREAM sous-jacents. Si une application doit ajouter de petits objets blob, écrivez ces derniers dans une colonne `varbinary(max)`, puis effectuez une opération d'écriture unique dans l'objet blob FILESTREAM lorsque le nombre d'objets blob atteint une limite prédéterminée.  
  
-   Évitez de récupérer la longueur des données de nombreux fichiers BLOB dans une application. Il s'agit d'une opération qui prend du temps, car la taille n'est pas stockée dans le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Pour déterminer la longueur d’un fichier BLOB, utilisez la fonction [!INCLUDE[tsql](../../includes/tsql-md.md)] DATALENGTH() afin de déterminer la taille du fichier BLOB, s’il est fermé. DATALENGTH() n’ouvre pas le fichier BLOB pour déterminer sa taille.  
  
-   Si une application utilise le protocole SMB1 (Message Block1), les données BLOB FILESTREAM doivent être lues par multiples de 60 Ko pour optimiser les performances.  
  
## <a name="see-also"></a>Voir aussi  
 [Éviter les conflits avec les opérations de base de données dans les applications FILESTREAM](avoid-conflicts-with-database-operations-in-filestream-applications.md)   
 [Accéder à des données FILESTREAM avec OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md)   
 [Objets binaires volumineux &#40;Objet BLOB&#41; Données &#40;SQL Server&#41;](binary-large-object-blob-data-sql-server.md)   
 [Effectuer des mises à jour partielles de données FILESTREAM](make-partial-updates-to-filestream-data.md)  
  
  
