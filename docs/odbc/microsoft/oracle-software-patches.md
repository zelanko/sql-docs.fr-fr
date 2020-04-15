---
title: Oracle Software Patches - France Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], Oraclesoftware patches
- Oracle software patches [ODBC]
ms.assetid: 1275157b-f4e1-4c24-b273-c02555e261c2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b1fb577e7b08f6ef332ed35f6d275a5f7ce543ba
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292949"
---
# <a name="oracle-software-patches"></a>Correctifs logiciels Oracle
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Patches pour les produits serveur Oracle et son composant client sont nécessaires pour le bon fonctionnement de plusieurs produits et technologies Microsoft, y compris le pilote Microsoft ODBC pour Oracle, le fournisseur Microsoft OLE DB pour Oracle, Internet Information Services (IIS), Component Services (ou Microsoft Transaction Server, si vous utilisez Windows NT), et ainsi de suite.  
  
> [!NOTE]  
>  Les instructions suivantes peuvent ne pas être tout à fait exactes parce que le site Oracle FTP est sujet à changement.  
  
### <a name="to-download-the-oracle-software-patches"></a>Pour télécharger les correctifs logiciels Oracle  
  
1.  Connectez-vous au site public FTP à oracle-ftp.oracle.com. L’identifiant de l’utilisateur est « anonyme » et le mot de passe est votre adresse e-mail.  
  
2.  Naviguez vers l’annuaire suivant : /serveur/wgt_tech/serveur/windowsNT.  
  
3.  Pour télécharger les correctifs les plus pertinents pour Windows 95, Windows 98 et Windows NT/Windows 2000, naviguez vers la sous-direction pour votre version d’Oracle - 7.3 ou 8.0. Les deux sous-directions sont /73patchsets et /80patchsets.  
  
4.  Pour télécharger des correctifs pour la technologie réseau d’Oracle, sqL-Net ou Net8, naviguez vers le répertoire suivant : /réseau.  
  
 L’accès à ce site FTP à partir de votre navigateur Web peut ne pas fonctionner. Si vous rencontrez des problèmes, essayez d’utiliser un client FTP « traditionnel » ou utilisez l’invite de commande DOS.  
  
> [!NOTE]  
>  Étant donné qu’Oracle répare les bogues dans les versions actuelles, puis les rénove à des versions antérieures à l’aide de correctifs logiciels, il est recommandé que vous téléchargez le dernier patch disponible. Cela est particulièrement vrai pour les composants Oracle Server Client. Si vous avez des questions sur l’installation de ces correctifs, contactez Oracle Support.
