---
title: Commande OLE DB, transformation | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.oledbcommandtrans.f1
helpviewer_keywords:
- statements [Integration Services]
- OLE DB Command transformation
ms.assetid: baa6735c-5acf-4759-b077-1216aca16c6c
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 3a8ffc33de161c71c6f72eebf8616d1e814fb994
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62770385"
---
# <a name="ole-db-command-transformation"></a>transformation de commande OLE DB
  La transformation de commande OLE DB exécute une instruction SQL pour chaque ligne d'un flux de données. Par exemple, vous pouvez exécuter une instruction SQL qui insère, met à jour ou supprime des lignes d'une table de base de données.  
  
 Vous pouvez configurer la transformation de commande OLE DB de plusieurs manières :  
  
-   Spécifiez l'instruction SQL exécutée par la transformation pour chaque ligne.  
  
-   Spécifiez le nombre de secondes accordées pour l'exécution de l'instruction SQL.  
  
-   Spécifiez la page de codes par défaut.  
  
 En général, l'instruction SQL inclut des paramètres. Les valeurs des paramètres sont stockées dans des colonnes externes dans l'entrée de transformation et le mappage d'une colonne d'entrée à une colonne externe mappe une colonne d'entrée à un paramètre. Par exemple, pour rechercher des lignes dans la table **DimProduct** par la valeur de leur colonne **ProductKey** et pour les supprimer, vous pouvez mapper la colonne externe nommée **Param_0** à la colonne d’entrée nommée **ProductKey** , puis exécuter l’instruction SQL `DELETE FROM DimProduct WHERE ProductKey = ?`. La transformation de commande OLE DB fournit les noms des paramètres, que vous ne pouvez pas modifier. Les noms des paramètres sont **Param_0**, **Param_1**et ainsi de suite.  
  
 Si vous configurez la transformation de commande OLE DB à l'aide de la boîte de dialogue **Éditeur avancé** , les paramètres de l'instruction SQL peuvent être mappés automatiquement à des colonnes externes dans l'entrée de transformation (et les caractéristiques de chaque paramètre définis) en cliquant sur le bouton **Actualiser** . Toutefois, si le fournisseur OLE DB utilisé par la transformation de commande OLE DB ne prend pas en charge la dérivation d'informations de paramètres à partir du paramètre, vous devez configurer les colonnes externes manuellement. Cela signifie que vous devez ajouter une colonne pour chaque paramètre à l’entrée externe de la transformation, mettre à jour les noms de colonnes de façon à utiliser des noms tels que **Param_0**, spécifier la valeur de la propriété DBParamInfoFlags, puis mapper les colonnes d’entrée qui contiennent des valeurs de paramètres aux colonnes externes.  
  
 La valeur de DBParamInfoFlags représente les caractéristiques du paramètre. Par exemple, la valeur **1** indique qu'il s'agit d'un paramètre d'entrée et la valeur **65** indique qu'il s'agit d'un paramètre d'entrée pouvant contenir une valeur nulle. Les valeurs doivent correspondre aux valeurs de l'énumération OLE DB DBPARAMFLAGSENUM. Pour plus d'informations, consultez la documentation de référence OLE DB.  
  
 La transformation de commande OLE DB inclut la propriété personnalisée `SQLCommand`. La propriété peut être mise à jour par une expression de propriété lors du chargement du package. Pour plus d’informations, consultez [Expressions Integration Services &#40;SSIS&#41; ](../../expressions/integration-services-ssis-expressions.md), [Expressions de propriété dans des packages](../../expressions/use-property-expressions-in-packages.md) et [Propriétés personnalisées des transformations](transformation-custom-properties.md).  
  
 Cette transformation a une entrée, une sortie standard et une sortie d'erreur.  
  
## <a name="logging"></a>Journalisation  
 Vous pouvez consigner les appels émis par la transformation de commande OLE DB vers les fournisseurs de données externes. Vous pouvez utiliser cette fonctionnalité de journalisation pour résoudre des problèmes liés aux connexions et aux commandes vers des sources de données externes effectuées par la transformation de commande OLE DB. Pour consigner les appels que la transformation de commande OLE DB adresse à des fournisseurs de données externes, activez la journalisation des packages et sélectionnez l'événement **Diagnostic** au niveau du package. Pour plus d’informations, consultez [Outils de dépannage pour l’exécution des packages](../../troubleshooting/troubleshooting-tools-for-package-execution.md).  
  
## <a name="related-tasks"></a>Tâches associées  
 Vous pouvez configurer la transformation à l'aide du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou du modèle objet. Pour plus d’informations sur la configuration de la transformation à l’aide du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] , consultez  [Configurer la transformation de commande OLE DB](../../configure-the-ole-db-command-transformation.md). Pour plus d'informations sur la configuration par programmation de cette transformation, consultez le Guide du développeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de données](../data-flow.md)   
 [Transformations Integration Services](integration-services-transformations.md)  
  
  
