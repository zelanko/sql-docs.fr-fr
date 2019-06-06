---
title: Open, méthode (ADO Stream) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_Open
- _Stream::Open
helpviewer_keywords:
- Open method [ADO]
ms.assetid: d26f48fb-904e-4932-a245-3b4332ca1600
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c1d1863b28367ba825541c6e334613f65d3bc657
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66707085"
---
# <a name="open-method-ado-stream"></a>Open, méthode (Stream ADO)
Ouvre un [Stream](../../../ado/reference/ado-api/stream-object-ado.md) objet à manipuler des flux de données binaires ou texte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.Open Source, Mode , OpenOptions, UserName, Password  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Source*  
 Facultatif. Un **Variant** valeur qui spécifie la source de données pour le **Stream**. *Source* peut contenir une chaîne d’URL absolue qui pointe vers un nœud existant dans une arborescence bien connu, tel qu’un système de fichiers ou de messagerie. Une URL doit être spécifiée à l’aide du mot clé URL (« URL =*schéma*://*server*/*dossier*»). Vous pouvez également *Source* peut contenir une référence à un déjà ouverte [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) objet, qui ouvre le flux par défaut associé à la **enregistrement**. Si *Source* n’est pas spécifié, un **Stream** est instancié et ouvert, associé à aucune source sous-jacent par défaut. Pour plus d’informations sur les schémas d’URL et leurs fournisseurs associés, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 *Mode*  
 Facultatif. Un [ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md) valeur qui spécifie le mode d’accès pour le résultant **Stream** (par exemple, en lecture/écriture ou en lecture seule). Valeur par défaut est **adModeUnknown**. Consultez le [Mode](../../../ado/reference/ado-api/mode-property-ado.md) propriété pour plus d’informations sur les modes d’accès. Si *Mode* n’est pas spécifié, il est hérité par l’objet source. Par exemple, si la source de **enregistrement** est ouvert en mode en lecture seule, le **Stream** sera également ouvert en mode lecture seule par défaut.  
  
 *OpenOptions*  
 Facultatif. Un [StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md) valeur. Valeur par défaut est **adOpenStreamUnspecified**.  
  
 *UserName*  
 Facultatif. Un **chaîne** valeur qui contient l’ID d’utilisateur qui, s’il est nécessaire, accède à la **Stream** objet.  
  
 *Mot de passe*  
 Facultatif. Un **chaîne** valeur qui contient le mot de passe, s’il est nécessaire, accède à la **Stream** objet.  
  
## <a name="remarks"></a>Notes  
 Quand un **enregistrement** objet est transmis comme paramètre source, le *UserID* et *mot de passe* paramètres ne sont pas utilisés, car l’accès à la **enregistrement** objet est déjà disponible. De même, le [Mode](../../../ado/reference/ado-api/mode-property-ado.md) de la **enregistrement** objet est transféré vers le **Stream** objet. Lorsque *Source* n’est pas spécifié, le **Stream** ouvert ne contient aucune donnée et a un [taille](../../../ado/reference/ado-api/size-property-ado-stream.md) de zéro (0). Pour éviter de perdre toutes les données sont écrites dans ce **Stream** lorsque le **Stream** est fermée, enregistrer le **Stream** avec la [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) ou [ SaveToFile](../../../ado/reference/ado-api/savetofile-method.md) méthodes, ou l’enregistrer sur un autre emplacement de mémoire.  
  
 Un *si OptionsOuverture a* valeur **adOpenStreamFromRecord** identifie le contenu de la *Source* paramètre soit déjà ouvert **enregistrement**objet. Le comportement par défaut consiste à traiter *Source* comme une URL qui pointe directement vers un nœud dans une structure arborescente, tel qu’un fichier. Le flux par défaut associé à ce nœud est ouvert.  
  
 Bien que le **Stream** est pas ouvert, il est possible de lire toutes les propriétés en lecture seule de la **Stream**. Si un **Stream** est ouvert de façon asynchrone, toutes les opérations suivantes (autres que la vérification du [état](../../../ado/reference/ado-api/state-property-ado.md) et d’autres propriétés en lecture seule) sont bloqués jusqu'à ce que le **Open** opération terminée.  
  
 Outre les options mentionnées précédemment, en ne spécifiant ne pas *Source*, vous pouvez créer une instance d’un **Stream** objet en mémoire sans l’associer à une source sous-jacente. Vous pouvez ajouter dynamiquement des données dans le flux en écrivant des données binaires ou de texte pour le **Stream** avec [écrire](../../../ado/reference/ado-api/write-method.md) ou [WriteText](../../../ado/reference/ado-api/writetext-method.md), ou en chargeant les données à partir d’un fichier avec [ LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md).  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Open, méthode (objet Connection ADO)](../../../ado/reference/ado-api/open-method-ado-connection.md)   
 [Open, méthode (objet Record ADO)](../../../ado/reference/ado-api/open-method-ado-record.md)   
 [Open, méthode (objet Recordset ADO)](../../../ado/reference/ado-api/open-method-ado-recordset.md)   
 [OpenSchema, méthode](../../../ado/reference/ado-api/openschema-method.md)   
 [SaveToFile, méthode](../../../ado/reference/ado-api/savetofile-method.md)
