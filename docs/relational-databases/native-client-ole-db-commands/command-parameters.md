---
title: Paramètres de commande | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- parameters [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, parameters
- SQL Server Native Client OLE DB provider, commands
- parameters [SQL Server Native Client], OLE DB
- commands [OLE DB]
ms.assetid: 072ead49-ebaf-41eb-9a0f-613e9d990f26
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5db24ee3b68d1a8989200479a3ce4018e63a5177
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304510"
---
# <a name="command-parameters"></a>Paramètres de commande
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Les paramètres sont marqués dans le texte de la commande avec le caractère de point d'interrogation. Par exemple, l'instruction SQL suivante est marquée pour un paramètre d'entrée unique :  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 Pour améliorer les performances en [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] réduisant le trafic réseau, le fournisseur de DB OLE Native Client ne tire pas automatiquement des informations sur les paramètres à moins **que ICommandWithParameters::GetParameterInfo** ou **ICommandPrepare::Prepare** est appelé avant d’exécuter une commande. Cela signifie [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que le fournisseur de DB OLE de client autochtone ne fait pas automatiquement :  
  
-   La vérification de ce que le type de données spécifié avec **ICommandWithParameters::SetParameterInfo** est correct.  
  
-   Mappage du DBTYPE spécifié dans les informations de liaison d'accesseur au type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] correct pour le paramètre.  
  
 Les applications recevront des erreurs ou présenteront une perte de précision avec l'une ou l'autre de ces méthodes si elles spécifient des types de données qui ne sont pas compatibles avec le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du paramètre.  
  
 Pour éviter cela, l'application doit :  
  
-   vérifier que *pwszDataSourceType* correspond au type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le paramètre en cas de codage en dur de **ICommandWithParameters::SetParameterInfo**.  
  
-   s'assurer que la valeur DBTYPE qui est liée au paramètre est du même type que le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le paramètre en cas de codage effectué de manière irréversible d'un accesseur ;  
  
-   coder l’application de façon à appeler **ICommandWithParameters::GetParameterInfo** afin que le fournisseur puisse obtenir dynamiquement les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des paramètres. Notez que cela provoque une boucle réseau supplémentaire au serveur.  
  
> [!NOTE]  
>  Le fournisseur ne prend pas en charge l’appel à **ICommandWithParameters::GetParameterInfo** pour les instructions UPDATE ou DELETE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenant une clause FROM ; pour les instructions SQL qui dépendent d’une sous-requête contenant des paramètres ; pour les instructions SQL contenant des marqueurs de paramètre dans les deux expressions d’un prédicat de comparaison, like ou quantifié ; ou les requêtes dans lesquelles un des paramètres est un paramètre d’une fonction. Lors du traitement d’un lot d’instructions SQL, le fournisseur ne prend pas non plus en charge l’appel à **ICommandWithParameters::GetParameterInfo** pour les marqueurs de paramètre dans les instructions après la première instruction du lot. Les commentaires (/* \*/) ne sont pas autorisés dans la commande [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE native Client prend en charge les paramètres d’entrée dans les commandes de relevés SQL. Sur les commandes d’appel de procédure, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE OLE de client autochtone prend en charge les paramètres d’entrée, de sortie et d’entrée/sortie. Les valeurs de paramètre de sortie sont retournées à l'application lors de l'exécution (uniquement si aucun ensemble de lignes n'est retourné) ou lorsque tous les ensembles de lignes retournés sont épuisés par l'application. Pour garantir que les valeurs retournées sont valides, utilisez **IMultipleResults** pour forcer la consommation de l’ensemble de lignes.  
  
 Les noms des paramètres de procédure stockée n'ont pas besoin d'être spécifiés dans une structure DBPARAMBINDINFO. Utilisez NULL pour la valeur du membre *pwszName* pour indiquer que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE Native Client devrait ignorer le nom du paramètre et n’utiliser que l’ordinaire spécifié dans le membre *rgParamOrdinals* d’ICommandWithParameters::SetParameterInfo . **ICommandWithParameters::SetParameterInfo** Si le texte de la commande contient à la fois des paramètres nommés et sans nom, tous les paramètres sans nom doivent être spécifiés avant les paramètres nommés.  
  
 Si le nom d’un paramètre [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de procédure stocké est spécifié, le fournisseur de DB OLE du client autochtone vérifie le nom pour s’assurer qu’il est valide. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de DB OLE de client autochtone renvoie une erreur lorsqu’il reçoit un nom de paramètre erroné du consommateur.  
  
> [!NOTE]  
>  Pour exposer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le support pour XML et les [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] types définis par l’utilisateur (UDT), le fournisseur native Client OLE DB implémente une nouvelle interface [ISSCommandWithParameters.](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
