---
title: CommandText, propriété (ADO) | Documents Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandText
helpviewer_keywords:
- CommandText property [ADO]
ms.assetid: 4dd7e82a-8da5-4a4e-b439-11a29286fa0e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c333cd961ea8b4b3f37f78c682ebe65c7ac9001
ms.sourcegitcommit: 62826c291db93c9017ae219f75c3cfeb8140bf06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35276858"
---
# <a name="commandtext-property-ado"></a>CommandText, propriété (ADO)
Indique le texte d’une commande pour être émise sur un fournisseur.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Obtient ou définit un **chaîne** valeur contenant une commande de fournisseur, comme une instruction SQL, un nom de table, une URL relative ou un appel de procédure stockée. La valeur par défaut est une chaîne vide (« »).  
  
## <a name="remarks"></a>Notes  
 Utilisez le **CommandText** propriété pour définir ou retourner le texte d’une commande représentée par un [commande](../../../ado/reference/ado-api/command-object-ado.md) objet. Généralement cela sera une instruction SQL, mais peut également être n’importe quel autre type d’instruction de commande reconnue par le fournisseur, tel qu’un appel de procédure stockée. Une instruction SQL doit être de la version prise en charge par le processeur de requêtes du fournisseur ou le dialecte particulier.  
  
 Si le [Prepared](../../../ado/reference/ado-api/prepared-property-ado.md) propriété de la **commande** objet a la valeur **True** et **commande** objet est lié à une connexion ouverte lorsque vous définissez le **CommandText** propriété, ADO prépare la requête (c'est-à-dire, une forme compilée de la requête est stockée par le fournisseur) lorsque vous appelez le [Execute](../../../ado/reference/ado-api/execute-method-ado-command.md) ou [ouvrir](../../../ado/reference/ado-api/open-method-ado-connection.md)méthodes.  
  
 Selon le [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) paramètre, de la propriété ADO peut modifier la **CommandText** propriété. Vous pouvez lire la **CommandText** propriété à tout moment pour voir le texte réel de la commande que ADO utilisent lors de l’exécution.  
  
 Utilisez le **CommandText** propriété pour définir ou retourner une URL relative qui spécifie une ressource, comme un fichier ou répertoire. La ressource est un emplacement spécifié explicitement par une URL absolue, ou implicitement par open [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet.  
  
> [!NOTE]
>  URL à l’aide du modèle http appellent automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Command, objet (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ActiveConnection, CommandText, CommandTimeout, CommandType, la taille et Direction, propriétés-exemple (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, la taille et Direction, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [Requery (méthode)](../../../ado/reference/ado-api/requery-method.md)   
 [ActiveConnection, CommandText, CommandTimeout, CommandType, la taille et Direction, propriétés-exemple (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
