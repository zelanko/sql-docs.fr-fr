---
title: Marquage d’objets métier comme sûrs pour l’écriture de scripts | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- business objects in RDS [ADO]
ms.assetid: 0be98d1a-ab3d-4dce-a166-dacda10d154a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0a8c6e3b1d74cb122a94cc643a9eb94d5dbb6c5c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47772717"
---
# <a name="marking-business-objects-as-safe-for-scripting"></a>Marquage d’objets métier comme sûrs pour l’écriture de scripts
> [!IMPORTANT]
>  Depuis Windows 8 et Windows Server 2012, composants de serveur Services Bureau à distance ne sont plus inclus dans le système d’exploitation Windows (voir Windows 8 et [Guide de compatibilité de Windows Server 2012](https://www.microsoft.com/en-us/download/details.aspx?id=27416) pour plus de détails). Composants du client RDS seront supprimées dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent des services Bureau à distance doivent migrer vers [Service de données WCF](http://go.microsoft.com/fwlink/?LinkId=199565).  
  
 Pour aider à sécuriser un environnement Internet, vous devez marquer les objets métier instanciés avec le [RDS. DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md) l’objet [CreateObject](../../../ado/reference/rds-api/createobject-method-rds.md) méthode comme étant « sécurisés pour le script ». Vous devez vous assurer qu’ils sont marqués comme tels dans la zone de la licence du Registre système avant de pouvoir être utilisés dans DCOM.  
  
> [!NOTE]
>  La mention « sécurisé pour le script » ou l’initialisation des objets métier peuvent être instanciés et initialisés par tout le monde sur le réseau. Marquer un objet métier « sécurisé pour le script » n’en fait pas sécurisée. Il est vital de s’assurer que les objets métier sont codées avec la sécurité la plus élevée pour vous assurer que ces objets ne présentent pas un point d’accès non protégé pour les données sensibles.  
  
 Pour configurer manuellement votre objet métier comme sûrs pour l’écriture de scripts, créez un fichier texte avec une extension .reg qui contient le texte suivant. Dans cet exemple, \< *MyActiveXGUID*> est le nombre GUID hexadécimal de votre objet métier. Les deux numéros suivants activer la fonctionnalité sécurisé pour le script :  
  
```  
[HKEY_CLASSES_ROOT\CLSID\<MyActiveXGUID>\Implemented   
Categories\{7DD95801-9882-11CF-9FA9-00AA006C42C4}]  
[HKEY_CLASSES_ROOT\CLSID\<MyActiveXGUID>\Implemented   
Categories\{7DD95802-9882-11CF-9FA9-00AA006C42C4}]  
```  
  
 Enregistrez le fichier et les fusionner dans votre Registre en utilisant l’Éditeur du Registre ou en double-cliquant sur le fichier .reg dans l’Explorateur Windows.  
  
 Les objets métier créés dans Microsoft Visual Basic peuvent automatiquement marquées comme étant « sécurisés pour le script » avec l’Assistant de déploiement et le Package. Lorsque l’Assistant vous invite à spécifier les paramètres de sécurité, sélectionnez **pour l’initialisation** et **sécurisé pour le script**.  
  
 Sur la dernière étape, l’Assistant crée un .htm et un fichier .cab. Vous pouvez copier ces deux fichiers à l’ordinateur cible, puis double-cliquez sur le fichier .htm pour charger la page et enregistrer correctement le serveur.  
  
 Étant donné que l’objet métier sera installé dans le répertoire Windows\System32\Occache par défaut, déplacez-le vers le répertoire Windows\System32 et modifier le **HKEY_CLASSES_ROOT\CLSID\\**  \< *MyActiveXGUID*>\\**InprocServer32** clé de Registre pour faire correspondre le chemin correct.


