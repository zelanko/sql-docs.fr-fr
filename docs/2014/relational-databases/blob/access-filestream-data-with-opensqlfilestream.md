---
title: Accéder à des données FILESTREAM avec OpenSqlFilestream | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: article
api_name:
- OpenSqlFilestream
api_location:
- sqlncli11.dll
helpviewer_keywords:
- OpenSqlFilestream
ms.assetid: d8205653-93dd-4599-8cdf-f9199074025f
caps.latest.revision: 45
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 81dab09c293fff8ad4d47df63a7069e48f63d638
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36045209"
---
# <a name="access-filestream-data-with-opensqlfilestream"></a>Accéder à des données FILESTREAM avec OpenSqlFilestream
  L’API OpenSqlFilestream Obtient un descripteur de fichier compatible Win32 pour un objet FILESTREAM (BLOB) stockées dans le système de fichiers. Le descripteur peut être passé à chacune des API Win32 suivantes : [ReadFile](http://go.microsoft.com/fwlink/?LinkId=86422), [WriteFile](http://go.microsoft.com/fwlink/?LinkId=86423), [TransmitFile](http://go.microsoft.com/fwlink/?LinkId=86424), [SetFilePointer](http://go.microsoft.com/fwlink/?LinkId=86425), [SetEndOfFile](http://go.microsoft.com/fwlink/?LinkId=86426)ou [FlushFileBuffers](http://go.microsoft.com/fwlink/?LinkId=86427). Si vous passez ce descripteur à une autre API Win32, l'erreur ERROR_ACCESS_DENIED est retournée. Le descripteur doit être fermé en le passant à l’API [CloseHandle](http://go.microsoft.com/fwlink/?LinkId=86428) Win32 avant que la transaction soit validée ou restaurée. Si le descripteur n'est pas fermé, il peut y avoir des fuites de ressources côté serveur.  
  
 Tous les accès de conteneur de données FILESTREAM doivent être effectuées dans un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction. [!INCLUDE[tsql](../../includes/tsql-md.md)] Vous pouvez également exécuter des instructions dans la même transaction. Cela maintient la cohérence entre les données SQL et les données BLOB FILESTREAM.  
  
 Pour accéder à l’objet BLOB FILESTREAM à l’aide de Win32, [l’Autorisation Windows](../security/choose-an-authentication-mode.md) doit être activée.  
  
> [!IMPORTANT]  
>  Lorsque le fichier est ouvert pour l'accès en écriture, la transaction appartient à l'agent FILESTREAM. Seule l'E/S de fichiers Win32 est autorisée tant que la transaction n'est pas débloquée. Pour débloquer la transaction, le descripteur d'écriture doit être fermé.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
  HANDLE OpenSqlFilestream (  
  LPCWSTR  
  FilestreamPath  
  ,  
  SQL_FILESTREAM_DESIRED_ACCESS  
  DesiredAccess,  
ULONGOpenOptions,LPBYTEFilestreamTransactionContext,SIZE_TFilestreamTransactionContextLength,PLARGE_INTEGERAllocationSize);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *FilestreamPath*  
 [in] Est la `nvarchar(max)` chemin d’accès qui est retourné par la [chemin d’accès](/sql/relational-databases/system-functions/pathname-transact-sql) (fonction). PathName doit être appelé à partir du contexte d’un compte qui dispose des autorisations [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] SELECT ou UPDATE sur la table et la colonne FILESTREAM.  
  
 *DesiredAccess*  
 [in] Définit le mode utilisé pour accéder aux données BLOB FILESTREAM. Cette valeur est passée à la [fonction DeviceIoControl](http://go.microsoft.com/fwlink/?LinkId=105527).  
  
|Nom   |Valeur|Signification|  
|----------|-----------|-------------|  
|SQL_FILESTREAM_READ|0|Les données peuvent être lues à partir du fichier.|  
|SQL_FILESTREAM_WRITE| 1|Les données peuvent être écrites dans le fichier.|  
|SQL_FILESTREAM_READWRITE|2|Les données peuvent être écrites dans le fichier et lues à partir de celui-ci.|  
  
> [!NOTE]  
>  Ces valeurs sont définies dans l'énumération SQL_FILESTREAM_DESIRED_ACCESS dans sqlncli.h.  
  
 *OpenOptions*  
 [in] Les attributs et indicateurs de fichier. Ce paramètre peut également inclure toute combinaison des indicateurs suivants.  
  
|Indicateur|Valeur|Signification|  
|----------|-----------|-------------|  
|SQL_FILESTREAM_OPEN_NONE|0x00000000:|Le fichier est ouvert ou créé sans options spéciales.|  
|SQL_FILESTREAM_OPEN_FLAG_ASYNC|0x00000001L|Le fichier est ouvert ou créé pour les E/S asynchrones.|  
|SQL_FILESTREAM_OPEN_FLAG_NO_BUFFERING|0x00000002L|Le système ouvre le fichier en n'utilisant aucune mise en cache système.|  
|SQL_FILESTREAM_OPEN_FLAG_NO_WRITE_THROUGH|0x00000004L|Le système n'écrit pas dans un cache intermédiaire. Il écrit directement sur le disque.|  
|SQL_FILESTREAM_OPEN_FLAG_SEQUENTIAL_SCAN|0x00000008L|Un fichier est accédé de manière séquentielle du début à la fin. Le système peut utiliser cette indication pour optimiser la mise en cache du fichier. Si une application déplace le pointeur de fichier pour l'accès aléatoire, la mise en cache optimale peut ne pas se produire.|  
|SQL_FILESTREAM_OPEN_FLAG_RANDOM_ACCESS|0x00000010L|Un fichier est accédé de manière aléatoire. Le système peut utiliser cette indication pour optimiser la mise en cache du fichier.|  
  
 *FilestreamTransactionContext*  
 [in] Valeur renvoyée par la fonction [GET_FILESTREAM_TRANSACTION_CONTEXT](/sql/t-sql/functions/get-filestream-transaction-context-transact-sql) .  
  
 *FilestreamTransactionContextLength*  
 [in] Nombre d’octets dans le `varbinary(max)` données retournées par la fonction GET_FILESTREAM_TRANSACTION_CONTEXT. La fonction retourne un tableau de N octets. N est déterminé par la fonction et est une propriété du tableau d'octets retourné.  
  
 *AllocationSize*  
 [in] Spécifie la taille d'allocation initiale du fichier de données en octets. Cet indicateur est ignoré en mode lecture. Ce paramètre peut être NULL, auquel cas le comportement de système de fichiers par défaut est utilisé.  
  
## <a name="return-value"></a>Valeur de retour  
 Si la fonction réussit, la valeur de retour est un descripteur ouvert vers un fichier spécifié. Si la fonction échoue, la valeur de retour est INVALID_HANDLE_VALUE. Pour obtenir plus d’informations sur les erreurs, appelez GetLastError().  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants indiquent comment utiliser l'API `OpenSqlFilestream` pour obtenir un descripteur Win32.  
  
 [!code-csharp[FILESTREAM#FS_CS_ReadAndWriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/cs/filestream.cs#fs_cs_readandwriteblob)]  
  
 [!code-vb[FILESTREAM#FS_VB_ReadAndWriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/vb/filestream.vb#fs_vb_readandwriteblob)]  
  
 [!code-cpp[FILESTREAM#FS_CPP_WriteBLOB](../../snippets/tsql/SQL15/tsql/filestream/cpp/filestream.cpp#fs_cpp_writeblob)]  
  
## <a name="remarks"></a>Notes  
 L'utilisation de cette API requiert l'installation du [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client est installé avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou les outils clients [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour plus d’informations, consultez [Installation de SQL Server Native Client](../native-client/applications/installing-sql-server-native-client.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Objets binaires volumineux &#40;Objet BLOB&#41; Données &#40;SQL Server&#41;](binary-large-object-blob-data-sql-server.md)   
 [Effectuer des mises à jour partielles de données FILESTREAM](make-partial-updates-to-filestream-data.md)   
 [Éviter les conflits avec les opérations de base de données dans les applications FILESTREAM](avoid-conflicts-with-database-operations-in-filestream-applications.md)  
  
  
