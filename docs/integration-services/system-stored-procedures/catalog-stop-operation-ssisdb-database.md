---
title: catalog.stop_operation (base de données SSISDB) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 97fd9d22-03dd-4eda-8f6c-ba8b67acec68
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: f7427a85fa3e8b6f65bb899d008a13f48008e4c0
ms.sourcegitcommit: fd71d04a9d30a9927cbfff645750ac9d5d5e5ee7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2019
ms.locfileid: "65715788"
---
# <a name="catalogstopoperation-ssisdb-database"></a>catalog.stop_operation (base de données SSISDB)

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Arrête une validation ou une instance d'exécution dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.stop_operation [ @operation_id = ] operation_id  
```  
  
## <a name="arguments"></a>Arguments  
 [ @operation_id = ] *operation_id*  
 Identificateur unique de la validation ou de l'instance d'exécution. *operation_id* est de type **bigint**.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'une des autorisations suivantes :  
  
-   Autorisations READ et MODIFY sur la validation ou l'instance d'exécution  
  
-   Appartenance au rôle de base de données **ssis_admin**  
  
-   Appartenance au rôle serveur **sysadmin**  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   L’utilisateur n’a pas les autorisations appropriées  
  
-   L'identificateur de l'opération n'est pas valide  
  
-   L'opération a déjà été arrêtée  
  
## <a name="remarks"></a>Notes   
 Un seul utilisateur à la fois doit arrêter une opération dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]. Si plusieurs utilisateurs essaient d'arrêter l'opération, la procédure stockée réussira (valeur `0`) à la première tentative, mais les tentatives suivantes généreront une erreur.  
  
  
