---
title: Open, méthode (objet Connection ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Connection15::raw_Open
- Connection15::Open
- _Connection::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: 663defab-5545-4973-9036-24d5882c9737
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 15115313613ea8f86dd2267c6be3c231cab92503
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931933"
---
# <a name="open-method-ado-connection"></a>Open, méthode (objet Connection ADO)
Ouvre une connexion à une source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
connection.Open ConnectionString, UserID, Password, Options  
```  
  
#### <a name="parameters"></a>Paramètres  
 *ConnectionString*  
 facultatif. Un **chaîne** valeur qui contient les informations de connexion. Consultez le [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) pour plus d’informations sur les paramètres valides.  
  
 *UserID*  
 facultatif. Un **chaîne** valeur qui contient un nom d’utilisateur à utiliser lors de l’établissement de la connexion.  
  
 *Mot de passe*  
 facultatif. Un **chaîne** valeur qui contient un mot de passe à utiliser lors de l’établissement de la connexion.  
  
 *Options*  
 facultatif. Un [ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md) valeur qui détermine si cette méthode doit retourner après (synchrone) ou avant (de façon asynchrone) la connexion est établie.  
  
## <a name="remarks"></a>Notes  
 À l’aide de la **Open** méthode sur un [connexion](../../../ado/reference/ado-api/connection-object-ado.md) objet établit la connexion physique à une source de données. Une fois que cette méthode se termine correctement, la connexion est établie et vous pouvez émettre des commandes sur elle et traiter les résultats.  
  
 Utilisez le paramètre facultatif *ConnectionString* argument pour spécifier une chaîne de connexion contenant une série de *argument* *= value* instructions séparées par des points-virgules, ou un fichier ou répertoire ressource identifiée par une URL. Le **ConnectionString** propriété hérite automatiquement de la valeur utilisée pour le *ConnectionString* argument. Par conséquent, vous pouvez soit définir le **ConnectionString** propriété de la **connexion** de l’objet avant de l’ouvrir, ou utiliser le *ConnectionString* argument pour définir ou substituer les paramètres de connexion en cours pendant la **Open** appel de méthode.  
  
 Si vous transmettez des informations utilisateur et mot de passe à la fois dans le *ConnectionString* argument et dans le paramètre facultatif *UserID* et *mot de passe* arguments, le *UserID*  et *mot de passe* arguments remplacent les valeurs spécifiées dans *ConnectionString*.  
  
 Lorsque vous avez terminé les opérations au moyen d’un **connexion**, utilisez le [fermer](../../../ado/reference/ado-api/close-method-ado.md) méthode pour libérer les ressources système d’associées. Fermeture d’un objet ne le supprime pas de la mémoire. Vous pouvez modifier ses paramètres de propriété et utiliser le **ouvrir** méthode pour l’ouvrir à nouveau ultérieurement. Pour éliminer complètement un objet de la mémoire, la valeur est la variable objet *rien*.  
  
> [!NOTE]
>  **L’utilisation à distance des services de données** lorsqu’il est utilisé sur une côté client **connexion** objet, le **Open** méthode réellement n’établit pas une connexion au serveur jusqu'à un [Recordset ](../../../ado/reference/ado-api/recordset-object-ado.md) est ouvert sur le **connexion** objet.  
  
> [!NOTE]
>  URL à l’aide du modèle http appellent automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Connection, objet (ADO MD)](../../../ado/reference/ado-api/connection-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Les méthodes Open et Close, exemple (VB)](../../../ado/reference/ado-api/open-and-close-methods-example-vb.md)   
 [Les méthodes Open et Close, exemple (VBScript)](../../../ado/reference/ado-api/open-and-close-methods-example-vbscript.md)   
 [Les méthodes Open et Close, exemple (VC ++)](../../../ado/reference/ado-api/open-and-close-methods-example-vc.md)   
 [Open, méthode (objet Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [Open, méthode (ADO Stream)](../../../ado/reference/ado-api/open-method-ado-stream.md)   
 [OpenSchema, méthode](../../../ado/reference/ado-api/openschema-method.md)
