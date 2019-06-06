---
title: LoadFromFile, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::raw_LoadFromFile
helpviewer_keywords:
- LoadFromFile method [ADO]
ms.assetid: b18d8d38-7354-4a94-b637-6ac035faa433
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ff7c5a2a2817fbe93d626ca7883107103edc58cd
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66694712"
---
# <a name="loadfromfile-method-ado"></a>LoadFromFile, méthode (ADO)
Charge le contenu d’un fichier existant dans un [Stream](../../../ado/reference/ado-api/stream-object-ado.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Stream.LoadFromFileFileName  
```  
  
#### <a name="parameters"></a>Paramètres  
 *FileName*  
 Un **chaîne** valeur qui contient le nom d’un fichier à charger dans le **Stream**. *Nom de fichier* peut contenir n’importe quel chemin d’accès valide et un nom au format UNC. Si le fichier spécifié n’existe pas, une erreur d’exécution se produit.  
  
## <a name="remarks"></a>Notes  
 Cette méthode peut être utilisée pour charger le contenu d’un fichier local dans un **Stream** objet. Cela peut servir à charger le contenu d’un fichier local sur un serveur.  
  
 Le **Stream** objet doit être déjà ouvert avant d’appeler **LoadFromFile**. Cette méthode ne modifie pas la liaison de la **Stream** objet ; il sera toujours lié à l’objet spécifié par l’URL ou **enregistrement** avec lequel le **Stream** était à l’origine ouvert.  
  
 **LoadFromFile** remplace le contenu actuel de la **Stream** objet avec les données lues à partir du fichier. Tous les octets dans le **Stream** sont remplacés par le contenu du fichier. Tous les octets restants et précédemment existants suivant le [EOS](../../../ado/reference/ado-api/eos-property.md) créé par **LoadFromFile**, sont tronqués.  
  
 Après un appel à **LoadFromFile**, la position actuelle est définie au début de la **Stream** ([Position](../../../ado/reference/ado-api/position-property-ado.md) est 0).  
  
 Étant donné que les 2 octets peut être ajoutés au début du flux de données pour l’encodage, la taille du flux de données peut différer la taille du fichier à partir duquel il a été chargé.  
  
## <a name="applies-to"></a>S'applique à  
 [Stream, objet (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)
