---
title: ConvertToString, méthode (RDS) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ConvertToString method [ADO]
ms.assetid: b3f36bc8-6f69-49b0-83cd-2ccd3afebfbe
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e88823d01e34a18bebe209f3939f8cb3532530f4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66712306"
---
# <a name="converttostring-method-rds"></a>ConvertToString, méthode (RDS)
Convertit un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) en chaîne MIME qui représente les données du jeu d’enregistrements.  
  
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DataFactory.ConvertToString(Recordset)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *DataFactory*  
 Une variable objet qui représente un [RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md) objet.  
  
 *Recordset*  
 Une variable objet qui représente un **Recordset** objet.  
  
## <a name="remarks"></a>Notes  
 Avec des fichiers .asp, utilisez **ConvertToString** pour incorporer le **Recordset** dans une page HTML générée sur le serveur pour le transfert vers un ordinateur client.  
  
 **ConvertToString** du premier chargement de la **Recordset** dans le Service de curseur tables, puis génère un flux au format MIME.  
  
 Sur le client, Service de données distant peut reconvertir la chaîne MIME entièrement fonctionnel **Recordset**. Il fonctionne bien pour gérer moins de 400 lignes de données avec pas plus de la largeur de 1 024 octets par ligne. Vous ne doit pas l’utiliser pour la diffusion en continu des données d’objets BLOB et des jeux de résultats volumineux via HTTP. Aucune compression simultanée n’est effectuée sur la chaîne, de très grands jeux de données prendra beaucoup de temps au transport sur HTTP par rapport au format tablegram optimisé de câble définis et déployés par le Service de données distant en tant que son format de protocole de transport natifs.  
  
> [!NOTE]
>  Si vous utilisez Active Server Pages pour incorporer la chaîne MIME résultante dans une page HTML de client, n’oubliez pas que les versions antérieures à la version 2.0 de VBScript limitent taille de la chaîne à 32 Ko. Si cette limite est dépassée, une erreur est retournée. Gardez à l’étendue de requête relativement faible lors de l’utilisation de l’incorporation de MIME via des fichiers .asp. Pour résoudre ce problème, téléchargez la dernière version de VBScript à partir du site Web Microsoft Windows Script Technologies.  
  
## <a name="applies-to"></a>S'applique à  
 [DataFactory, objet (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)  
  
## <a name="see-also"></a>Voir aussi  
 [ConvertToString, méthode-exemple (VB)](../../../ado/reference/ado-api/converttostring-method-example-vb.md)   
 [ConvertToString, exemple de méthode (VBScript)](../../../ado/reference/rds-api/converttostring-method-example-vbscript.md)


