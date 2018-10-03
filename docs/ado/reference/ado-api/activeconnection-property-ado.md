---
title: ActiveConnection, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::ActiveConnection
- Recordset15::get_ActiveConnection
- _Record::ActiveConnection
helpviewer_keywords:
- ActiveConnection property [ADO]
ms.assetid: 52d0a96c-14fb-4ad9-b004-4d821bc0a6db
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 951f43a2842162aa00f664dc83b754d06d8aafb2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47684337"
---
# <a name="activeconnection-property-ado"></a>ActiveConnection, propriété (ADO)
Indique à laquelle [connexion](../../../ado/reference/ado-api/connection-object-ado.md) spécifié de l’objet [commande](../../../ado/reference/ado-api/command-object-ado.md), [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), ou [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet appartient actuellement.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **chaîne** valeur qui contient une définition pour une connexion si la connexion est fermée, ou un **Variant** contenant actuel **connexion** si l’objet le connexion est ouverte. Valeur par défaut est une référence d’objet null. Consultez le [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) propriété.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **ActiveConnection** propriété afin de déterminer la **connexion** objet sur lequel spécifié **commande** objet exécutera ou spécifié  **Jeu d’enregistrements** s’ouvre.  
  
## <a name="command"></a>Command  
 Pour **commande** objets, le **ActiveConnection** propriété est en lecture/écriture.  
  
 Si vous essayez d’appeler le [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) méthode sur un **commande** objet avant de définir cette propriété pour une ouverture **connexion** objet ou la chaîne de connexion valide, une erreur se produit.  
  
 Si un **connexion** objet est assigné à la **ActiveConnection** propriété, l’objet doit être ouvert. Assignation d’un objet de connexion fermé provoque une erreur.  
  
### <a name="note"></a>Remarque  
 **Microsoft Visual Basic** paramètre la **ActiveConnection** propriété *rien* dissocie le **commande** objet à partir du **Connexion** et le fournisseur libérer les ressources associées dans la source de données. Vous pouvez ensuite associer la **commande** objet avec le même ou un autre **connexion** objet. Certains fournisseurs vous permettent de modifier le paramètre de propriété à partir d’un **connexion** vers un autre, sans devoir tout d’abord définir la propriété sur *rien*.  
  
 Si le [paramètres](../../../ado/reference/ado-api/parameters-collection-ado.md) collection de la **commande** objet contient les paramètres fournis par le fournisseur, la collection est effacée si vous définissez la **ActiveConnection** propriété *rien* ou à un autre **connexion** objet. Si vous créez manuellement [paramètre](../../../ado/reference/ado-api/parameter-object.md) les objets et les utiliser pour remplir la **paramètres** collection de la **commande** objet, en définissant le **ActiveConnection**  propriété *rien* ou à un autre **connexion** laisse l’objet le **paramètres** collection intacte.  
  
 Fermeture de la **connexion** objet avec lequel un **commande** objet est associé à des jeux le **ActiveConnection** propriété *rien*. Définition de cette propriété à un fermé **connexion** objet génère une erreur.  
  
## <a name="recordset"></a>Ensemble d'enregistrements  
 Pour ouvrir **Recordset** objets ou pour **Recordset** objets dont la propriété [Source](../../../ado/reference/ado-api/source-property-ado-recordset.md) propriété est définie sur valide **commande** (objet), le **ActiveConnection** propriété est en lecture seule. Sinon, il est en lecture/écriture.  
  
 Vous pouvez définir cette propriété sur valide **connexion** objet ou une chaîne de connexion valide. Dans ce cas, le fournisseur crée un **connexion** de l’objet à l’aide de cette définition et ouvre la connexion. En outre, le fournisseur peut définir cette propriété pour le nouveau **connexion** objet afin de vous donner un moyen d’accéder à la **connexion** pour des informations d’erreur étendues, ou pour exécuter d’autres commandes de l’objet.  
  
 Si vous utilisez le *ActiveConnection* argument de la [ouvrir](../../../ado/reference/ado-api/open-method-ado-recordset.md) méthode pour ouvrir un **Recordset** objet, le **ActiveConnection** propriété dont la valeur hériter de la valeur de l’argument.  
  
 Si vous définissez la **Source** propriété de la **Recordset** objet valide **commande** variable objet, le **ActiveConnection** propriété de le **Recordset** hérite du paramètre de la **commande** l’objet **ActiveConnection** propriété.  
  
> [!NOTE]
>  **Utilisation de Service de données à distance** lorsqu’il est utilisé sur une côté client **Recordset** de l’objet, cette propriété peut être définie qu’une chaîne de connexion ou (dans Microsoft Visual Basic ou Visual Basic, Scripting Edition) pour *Nothing* .  
  
## <a name="record"></a>Record  
 Cette propriété est en lecture/écriture lors de la **enregistrement** objet est fermé et peut contenir une chaîne de connexion ou une référence à une ouverture **connexion** objet. Cette propriété est en lecture seule lorsque le **enregistrement** objet est ouvert et contient une référence à une ouverture **connexion** objet.  
  
 Un **connexion** objet est créé implicitement lorsque la **enregistrement** objet est ouverte à partir d’une URL. Ouvrez le **enregistrement** avec un existant, ouvrez **connexion** objet en affectant le **connexion** de l’objet à cette propriété, ou à l’aide de la **connexion** objet en tant que paramètre dans le [Open](../../../ado/reference/ado-api/open-method-ado-record.md) appel de méthode. Si le **enregistrement** est ouverte à partir d’un existant **enregistrement** ou [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md), puis il est automatiquement associé **enregistrement** ou  **Jeu d’enregistrements** l’objet **connexion** objet.  
  
> [!NOTE]
>  URL à l’aide du modèle http appellent automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>S'applique à  
  
||||  
|-|-|-|  
|[Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Record, objet (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|[Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, la taille et Direction, propriétés-exemple (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, taille et Direction, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, la taille et Direction, propriétés-exemple (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)   
 [Objet Connection (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [ConnectionString, propriété (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)
