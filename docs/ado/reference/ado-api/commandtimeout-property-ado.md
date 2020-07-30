---
title: CommandTimeout, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandTimeout
helpviewer_keywords:
- CommandTimeout property [ADO]
ms.assetid: c611f857-d6b0-4dca-8925-f4a02e769eb0
author: rothja
ms.author: jroth
ms.openlocfilehash: 0b708b2b79c22240468811732d2ffae0955ea204
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87242779"
---
# <a name="commandtimeout-property-ado"></a>CommandTimeout, propriété (ADO)
Indique le délai d’attente lors de l’exécution d’une commande avant de mettre fin à la tentative et de générer une erreur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne une valeur de **type long** qui indique, en secondes, le délai d’attente avant l’exécution d’une commande. La valeur par défaut est 30.  
  
## <a name="remarks"></a>Notes  
 Utilisez la propriété **CommandTimeout** sur un objet de [connexion](../../../ado/reference/ado-api/connection-object-ado.md) ou un objet de [commande](../../../ado/reference/ado-api/command-object-ado.md) pour autoriser l’annulation d’un appel de méthode [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) , en raison de retards du trafic réseau ou de l’utilisation intensive du serveur. Si l’intervalle défini dans la propriété **CommandTimeout** s’écoule avant la fin de l’exécution de la commande, une erreur se produit et ADO annule la commande. Si vous affectez à la propriété la valeur zéro, ADO attend indéfiniment que l’exécution soit terminée. Assurez-vous que le fournisseur et la source de données dans lesquels vous écrivez le code prennent en charge la fonctionnalité **CommandTimeout** .  
  
 Le paramètre **CommandTimeout** sur un **objet Connection** n’a aucun effet sur le paramètre **CommandTimeout** sur un objet **Command** sur la même **connexion**; autrement dit, la propriété **CommandTimeout** de l’objet de **commande** n’hérite pas de la valeur de **CommandTimeout** de l’objet de **connexion** .  
  
 Sur un objet de **connexion** , la propriété **CommandTimeout** reste en lecture/écriture une fois la **connexion** ouverte.  
  
## <a name="applies-to"></a>S'applique à  

:::row:::
    :::column:::
        [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
    :::column-end:::
    :::column:::
        [Connection, objet (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)  
    :::column-end:::
:::row-end:::

## <a name="see-also"></a>Voir aussi  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, size et direction, exemple de propriétés (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, size et direction, exemple de propriétés (VC + +)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, size et direction, exemple de propriétés (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [ConnectionTimeout, propriété (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)
