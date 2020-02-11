---
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c88b8029ee5d96986cf9b366bd8faee53ca1393b
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67963228"
---
# <a name="url-property-rds"></a>URL, propriété (RDS)
Indique une chaîne qui contient une URL relative ou absolue.  
  
 Vous pouvez définir la propriété **URL** au moment de la conception dans la balise Object de l’objet [DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md) , ou au moment de l’exécution dans le code de script.  
  
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
 En règle générale, l’URL identifie un fichier de page de Active Server (. asp) qui peut produire et retourner un [jeu d’enregistrements](../../../ado/reference/ado-api/recordset-object-ado.md). Par conséquent, l’utilisateur peut obtenir un **jeu d’enregistrements** sans avoir à appeler l’objet [DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) côté serveur, ou à programmer un objet métier personnalisé.  
  
 Si la propriété **URL** a été définie, [SubmitChanges](../../../ado/reference/rds-api/submitchanges-method-rds.md) envoie les modifications à l’emplacement spécifié par l’URL.  
  
## <a name="applies-to"></a>S'applique à  
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>Voir aussi  
 [URL, exemple de propriété (VBScript)](../../../ado/reference/rds-api/url-property-example-vbscript.md)


