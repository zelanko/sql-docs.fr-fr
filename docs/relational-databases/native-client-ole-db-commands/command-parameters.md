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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3eb6ce3b08f8a1681906646eaa0c3498410582bc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63012685"
---
# <a name="command-parameters"></a>Paramètres de commande
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Les paramètres sont marqués dans le texte de la commande avec le caractère de point d'interrogation. Par exemple, l'instruction SQL suivante est marquée pour un paramètre d'entrée unique :  
  
```  
{call SalesByCategory('Produce', ?)}  
```  
  
 Pour améliorer les performances en réduisant le trafic réseau, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif ne dérive pas automatiquement les informations sur les paramètres, sauf si **ICommandWithParameters::GetParameterInfo** ou  **ICommandPrepare::Prepare** est appelée avant d’exécuter une commande. Cela signifie que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif n’effectue pas automatiquement :  
  
-   La vérification de ce que le type de données spécifié avec **ICommandWithParameters::SetParameterInfo** est correct.  
  
-   Mappage du DBTYPE spécifié dans les informations de liaison d'accesseur au type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] correct pour le paramètre.  
  
 Les applications recevront des erreurs ou présenteront une perte de précision avec l'une ou l'autre de ces méthodes si elles spécifient des types de données qui ne sont pas compatibles avec le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] du paramètre.  
  
 Pour éviter cela, l'application doit :  
  
-   vérifier que *pwszDataSourceType* correspond au type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le paramètre en cas de codage en dur de **ICommandWithParameters::SetParameterInfo**.  
  
-   s'assurer que la valeur DBTYPE qui est liée au paramètre est du même type que le type de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour le paramètre en cas de codage effectué de manière irréversible d'un accesseur ;  
  
-   coder l’application de façon à appeler **ICommandWithParameters::GetParameterInfo** afin que le fournisseur puisse obtenir dynamiquement les types de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] des paramètres. Notez que cela provoque une boucle réseau supplémentaire au serveur.  
  
> [!NOTE]  
>  Le fournisseur ne prend pas en charge l’appel à **ICommandWithParameters::GetParameterInfo** pour les instructions UPDATE ou DELETE [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] contenant une clause FROM ; pour les instructions SQL qui dépendent d’une sous-requête contenant des paramètres ; pour les instructions SQL contenant des marqueurs de paramètre dans les deux expressions d’un prédicat de comparaison, like ou quantifié ; ou les requêtes dans lesquelles un des paramètres est un paramètre d’une fonction. Lors du traitement d’un lot d’instructions SQL, le fournisseur ne prend pas non plus en charge l’appel à **ICommandWithParameters::GetParameterInfo** pour les marqueurs de paramètre dans les instructions après la première instruction du lot. Les commentaires (/* \*/) ne sont pas autorisés dans la commande [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge les paramètres d’entrée dans les commandes d’instruction SQL. Sur les commandes d’appel de procédure, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif prend en charge l’entrée, sortie et les paramètres d’entrée/sortie. Les valeurs de paramètre de sortie sont retournées à l'application lors de l'exécution (uniquement si aucun ensemble de lignes n'est retourné) ou lorsque tous les ensembles de lignes retournés sont épuisés par l'application. Pour garantir que les valeurs retournées sont valides, utilisez **IMultipleResults** pour forcer la consommation de l’ensemble de lignes.  
  
 Les noms des paramètres de procédure stockée n'ont pas besoin d'être spécifiés dans une structure DBPARAMBINDINFO. Utilisez NULL pour la valeur de la *pwszName* membre pour indiquer que le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif doit ignorer le nom du paramètre et utiliser uniquement l’ordinal spécifié dans le *rgParamOrdinals*membre **ICommandWithParameters::SetParameterInfo**. Si le texte de la commande contient à la fois des paramètres nommés et sans nom, tous les paramètres sans nom doivent être spécifiés avant les paramètres nommés.  
  
 Si le nom d’un paramètre de procédure stockée est spécifié, le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Client fournisseur OLE DB natif vérifie le nom pour vous assurer qu’il est valide. Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les fournisseur OLE DB Native Client retourne une erreur lorsqu’il reçoit un nom de paramètre erroné du consommateur.  
  
> [!NOTE]  
>  Pour exposer la prise en charge de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] XML et les types définis par l’utilisateur (UDT), le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fournisseur de OLE DB Native Client implémente une nouvelle [ISSCommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/isscommandwithparameters-ole-db.md) interface.  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes](../../relational-databases/native-client-ole-db-commands/commands.md)  
  
  
