---
description: URL, propriété (RDS)
title: URL, propriété (RDS) | Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- URL property [ADO]
ms.assetid: 8c56b233-1be8-442c-8d0e-a4c96465bc99
author: rothja
ms.author: jroth
ms.openlocfilehash: 5f0db677fcd63e3532553f0051ba88930d0f5c8a
ms.sourcegitcommit: 7345e4f05d6c06e1bcd73747a4a47873b3f3251f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2020
ms.locfileid: "88767268"
---
# <a name="url-property-rds"></a>URL, propriété (RDS)
Indique une chaîne qui contient une URL relative ou absolue.  
  
 Vous pouvez définir la propriété **URL** au moment de la conception dans la balise Object de l’objet [DataControl](./datacontrol-object-rds.md) , ou au moment de l’exécution dans le code de script.  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Design time: <PARAM NAME="URL" VALUE="Server">  
Run time: DataControl.URL="Server"  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Serveur*  
 Valeur de **chaîne** qui contient une URL valide.  
  
 *DataControl*  
 Variable objet qui représente un objet **DataControl** .  
  
## <a name="remarks"></a>Notes  
 En règle générale, l’URL identifie un fichier de page de Active Server (. asp) qui peut produire et retourner un [jeu d’enregistrements](../ado-api/recordset-object-ado.md). Par conséquent, l’utilisateur peut obtenir un **jeu d’enregistrements** sans avoir à appeler l’objet [DataFactory](./datafactory-object-rdsserver.md) côté serveur, ou à programmer un objet métier personnalisé.  
  
 Si la propriété **URL** a été définie, [SubmitChanges](./submitchanges-method-rds.md) envoie les modifications à l’emplacement spécifié par l’URL.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](./datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [URL, exemple de propriété (VBScript)](./url-property-example-vbscript.md)