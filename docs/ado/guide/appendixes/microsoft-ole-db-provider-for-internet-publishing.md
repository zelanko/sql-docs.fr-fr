---
title: Fournisseur Microsoft OLE DB pour la publication Internet | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB provider for Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
- Internet Publishing provider [ADO]
ms.assetid: 66a208d9-b580-4655-a41e-1d36e5b5bfca
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 19d719ddb4e5a2f7851a1d12dc4abe69069a354f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67926754"
---
# <a name="microsoft-ole-db-provider-for-internet-publishing-overview"></a>Fournisseur Microsoft OLE DB pour une vue d’ensemble de la publication Internet
Le fournisseur Microsoft OLE DB pour la publication Internet permet à ADO pour accéder aux ressources prises en charge par Microsoft FrontPage ou Microsoft Internet Information Server. Les ressources incluent les fichiers de sources de web tels que les fichiers HTML ou des dossiers web de Windows 2000.

## <a name="connection-string-parameters"></a>Paramètres de chaîne de connexion
 Pour vous connecter à ce fournisseur, définissez le *fournisseur* argument de la [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) propriété :

```vb
MSDAIPP.DSO
```

 Cette valeur peut également être définie ou lire à l’aide de la [fournisseur](../../../ado/reference/ado-api/provider-property-ado.md) propriété.

## <a name="typical-connection-string"></a>Chaîne de connexion classique
 Une chaîne de connexion classique pour ce fournisseur est :

```vb
"Provider=MSDAIPP.DSO;Data Source=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 ou

```vb
"URL=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 La chaîne se compose de ces mots clés :

|Mot clé|Description|
|-------------|-----------------|
|**Fournisseur**|Spécifie le fournisseur OLE DB pour la publication Internet.|
|**Source de données** - ou - **URL**|Spécifie l’URL d’un fichier ou un répertoire publié dans un dossier Web.|
|**ID d'utilisateur**|Spécifie le nom d’utilisateur.|
|**Mot de passe**|Spécifie le mot de passe utilisateur.|

> [!NOTE]
>  Si vous vous connectez à un fournisseur de source de données qui prend en charge l’authentification Windows, vous devez spécifier **Trusted_Connection = yes** ou **Integrated Security = SSPI** au lieu des ID d’utilisateur et mot de passe informations dans la chaîne de connexion.

 Si vous définissez la *ResourceURL ne* valeur à partir de le « URL = » dans la chaîne de connexion à une valeur non valide, par défaut le fournisseur de publication Internet déclenche une boîte de dialogue pour demander une valeur valide. Il s’agit d’un comportement indésirable pour un composant dans la couche intermédiaire d’une application, car il suspend l’exécution du programme jusqu'à ce que la boîte de dialogue est désactivée et le client se bloque, car il n’a pas reçu de réponse à partir du composant.

> [!NOTE]
>  Si MSDAIPP. DSO est explicitement spécifié comme valeur du fournisseur, soit avec le *fournisseur* mot clé de chaîne de connexion ou le **fournisseur** propriété, vous ne pouvez pas utiliser « URL = » dans la chaîne de connexion. Si vous le faites, une erreur se produit. Au lieu de cela, spécifiez simplement l’URL comme indiqué dans la rubrique [à l’aide d’ADO avec le fournisseur OLE DB pour la publication Internet](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md).

## <a name="see-also"></a>Voir aussi
 [Scénario de publication Internet](../../../ado/guide/data/internet-publishing-scenario.md) [du fournisseur OLE DB pour la publication Internet](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)
