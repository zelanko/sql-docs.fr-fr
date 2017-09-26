---
title: Catalog.create_execution_dump | Documents Microsoft
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: language-reference
ms.assetid: 91319b0b-5536-4ab4-a403-9559ed9dd177
caps.latest.revision: 12
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: b05e1b46845c0a2b5ee47b94dc239d79d4a12a17
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="catalogcreateexecutiondump"></a>catalog.create_execution_dump
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Provoque la suspension d'un package en cours d'exécution et la création d'un fichier de vidage par ce dernier. Le fichier est stocké dans le * \<lecteur >*: dossier \Program Files\Microsoft SQL Server\130\Shared\ErrorDumps.  
  
## <a name="syntax"></a>Syntaxe  
  
```tsql  
create_execution_dump [ @execution_id = ] execution_id  
  
```  
  
## <a name="arguments"></a>Arguments  
 [ @execution_id =] *execution_id*  
 ID d'exécution du package en cours d'exécution. Le *execution_id* est **bigint**.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, le package en cours d'exécution dont l'ID d'exécution est 88 est invité à créer un fichier de vidage.  
  
```  
  
EXEC create_execution_dump @execution_id = 88  
  
```  
  
## <a name="return-codes"></a>Codes de retour  
 0 (succès)  
  
 Lorsque la procédure stockée échoue, elle génère une erreur.  
  
## <a name="result-set"></a>Jeu de résultats  
 Aucune  
  
## <a name="permissions"></a>Permissions  
 Cette procédure stockée requiert des utilisateurs qui seront membres de la **ssis_admin** rôle de base de données.  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit les conditions provoquant l'échec de la procédure stockée.  
  
-   L'ID d'exécution spécifié n'est pas valide.  
  
-   Le package a déjà été exécuté.  
  
-   Le package crée actuellement un fichier de vidage.  
  
## <a name="see-also"></a>Voir aussi  
 [Générer de fichiers de vidage pour l’exécution des packages](../../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
