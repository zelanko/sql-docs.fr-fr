---
title: Stream, objet (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Stream
helpviewer_keywords:
- Stream object [ADO]
ms.assetid: 0514531f-009d-4519-abc3-d727014a39f1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 509f91b3e19b8e1215919ce89a98c6ac1c8fc74f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710756"
---
# <a name="stream-object-ado"></a>Stream, objet (ADO)
Représente un flux de données binaires ou de texte.  
  
 Dans les hiérarchies arborescence comme un système de fichiers ou un système de messagerie, en un [enregistrement](../../../ado/reference/ado-api/record-object-ado.md) peut être un flux de binaire par défaut de bits associé qui contient le contenu du fichier ou le message électronique. Un **Stream** objet peut être utilisé pour manipuler des champs ou enregistrements contenant ces flux de données. Un **Stream** objet peut être obtenu des façons suivantes :  
  
-   À partir d’une URL pointant vers un objet (généralement un fichier) contenant des données binaires ou texte. Cet objet peut être un document simple, un **enregistrement** objet représentant un document structuré ou un dossier.  
  
-   En ouvrant la valeur par défaut **Stream** objet associé à un **enregistrement** objet. Vous pouvez obtenir le flux par défaut associé à un **enregistrement** objet lorsque le **enregistrement** est ouvert, afin d’éliminer un aller-retour pour ouvrir le flux.  
  
-   En instanciant un **Stream** objet. Ces **Stream** objets peuvent être utilisés pour stocker les données dans le cadre de votre application. Contrairement à un **Stream** associé à une URL ou la valeur par défaut **Stream** d’un **enregistrement**, un instancié **Stream** ne possède aucune association avec un source sous-jacente par défaut.  
  
 Les méthodes et les propriétés d’un **Stream** de l’objet, vous pouvez procédez comme suit :  
  
-   Ouvrir un **Stream** à partir de l’objet une **enregistrement** ou URL avec le [Open](../../../ado/reference/ado-api/open-method-ado-stream.md) (méthode).  
  
-   Fermer un **Stream** avec la [fermer](../../../ado/reference/ado-api/close-method-ado.md) (méthode).  
  
-   Entrer des octets ou texte à un **Stream** avec la [écrire](../../../ado/reference/ado-api/write-method.md) et [WriteText](../../../ado/reference/ado-api/writetext-method.md) méthodes.  
  
-   Lire les octets à partir de la **Stream** avec la [en lecture](../../../ado/reference/ado-api/read-method.md) et [ReadText](../../../ado/reference/ado-api/readtext-method.md) méthodes.  
  
-   Écrivez une **Stream** du tampon de données toujours dans l’ADO.NET à l’objet sous-jacent avec le [vider](../../../ado/reference/ado-api/flush-method-ado.md) (méthode).  
  
-   Copiez le contenu d’un **Stream** vers un autre **Stream** avec la [CopyTo](../../../ado/reference/ado-api/copyto-method-ado.md) (méthode).  
  
-   Contrôler la façon dont les lignes sont lues à partir du fichier source avec le [SkipLine](../../../ado/reference/ado-api/skipline-method.md)(méthode) et le [LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md) propriété.  
  
-   Déterminer la position de fin de flux avec le [EOS](../../../ado/reference/ado-api/eos-property.md)propriété et [SetEOS](../../../ado/reference/ado-api/seteos-method.md) (méthode).  
  
-   Enregistrer et restaurer des données dans les fichiers avec le [SaveToFile](../../../ado/reference/ado-api/savetofile-method.md)et [LoadFromFile](../../../ado/reference/ado-api/loadfromfile-method-ado.md) méthodes.  
  
-   Spécifier le jeu de caractères utilisé pour stocker le **Stream** avec la [Charset](../../../ado/reference/ado-api/charset-property-ado.md) propriété.  
  
-   HALT asynchrone **Stream** opération avec le [Annuler](../../../ado/reference/ado-api/cancel-method-ado.md) (méthode).  
  
-   Déterminer le nombre d’octets dans un **Stream** avec la [taille](../../../ado/reference/ado-api/size-property-ado-stream.md) propriété.  
  
-   Contrôler la position actuelle dans un **Stream** avec la [Position](../../../ado/reference/ado-api/position-property-ado.md) propriété.  
  
-   Déterminer le type de données dans un **Stream** avec la [Type](../../../ado/reference/ado-api/type-property-ado-stream.md) propriété.  
  
-   Déterminer l’état actuel de la **Stream** (fermé, ouvrir, ou l’exécution) avec le [état](../../../ado/reference/ado-api/state-property-ado.md) propriété.  
  
-   Spécifier le mode d’accès pour le **Stream** avec la [Mode](../../../ado/reference/ado-api/mode-property-ado.md) propriété.  
  
> [!NOTE]
>  URL à l’aide du modèle http appellent automatiquement le [fournisseur Microsoft OLE DB pour la publication Internet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md). Pour plus d’informations, consultez [URL absolues et relatives](../../../ado/guide/data/absolute-and-relative-urls.md).  
  
 Le **Stream** objet est sécurisé pour le script.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Propriétés de l’objet Stream, méthodes et événements](../../../ado/reference/ado-api/stream-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Enregistrements et flux](../../../ado/guide/data/records-and-streams.md)
