---
title: Pont MRTK Figma pour Unity
description: MRTK Figma Bridge pour unity vous permet de mettre la disposition de Figma Shared Computer Toolkit dans unity
author: dongpark
ms.author: dongpark
ms.date: 03/29/2021
ms.topic: article
keywords: Figma, croquis, Adobe XD, design, designer, fichier de conception, conception UX, HoloLens, MRTK, réalité mixte Shared Computer Toolkit
ms.openlocfilehash: d21caa796907ebc7ea1fb46ce940cf210e9fc49d
ms.sourcegitcommit: 9431e9d6d7e959954ab3e18ecc0e420a3583d1a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2021
ms.locfileid: "128053806"
---
# <a name="mrtk-figma-bridge-for-unity-beta"></a>MRTK Figma Bridge pour Unity (bêta)

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWKiO4]

MRTK Figma Bridge pour unity vous permet de mettre la disposition de Figma Shared Computer Toolkit dans unity. le pont peut importer la disposition de l’interface utilisateur créée avec MRTK Figma Shared Computer Toolkit, puis instancie le prefabs MRTK correspondant avec la position et la taille appropriées. Figma Bridge aidera à concevoir le processus d’intégration et la collaboration entre les concepteurs et les développeurs.


consultez [MRTK Figma Shared Computer Toolkit](figma-toolkit.md) page pour en savoir plus sur Figma Shared Computer Toolkit qui est le fichier de conception avec HoloLens 2 bibliothèque d’interface utilisateur de style.

## <a name="prerequisites"></a>Prérequis
- Consultez [installer les outils](/windows/mixed-reality/develop/install-the-tools) pour les logiciels requis pour le développement de la réalité mixte
- Unity 2019 ou version ultérieure
- [MRTK-Unity 2.7.0 ou version ultérieure](/windows/mixed-reality/mrtk-unity/)

> [!IMPORTANT]
> **Requiert MRTK-Unity 2.7.0 ou une version ultérieure**
> 
> étant donné que Figma Shared Computer Toolkit et Figma Bridge sont basés sur MRTK 2.7.0 prefabs, MRTK 2.7.0 ou une version ultérieure est requis. Lorsqu’ils sont utilisés avec une version antérieure de MRTK, certains composants ne sont pas traduits correctement.

## <a name="how-to-use-mrtk-figma-bridge"></a>Utilisation de MRTK Figma Bridge

### <a name="1-installation"></a>1. installation

Figma Unity Bridge peut être installé par le biais de l’outil de la [fonctionnalité de réalité mixte](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool). Téléchargez et exécutez l’outil de la fonctionnalité de réalité mixte.

dans la page **découvrir les fonctionnalités** , sous la section Shared Computer Toolkit de la **réalité mixte** , sélectionnez **pont MRTK Figma unity Bridge**. Suivez les étapes pour terminer l’outil de fonctionnalité de MR et revenir à votre projet Unity. Unity importera le package pour MRTK Figma Bridge.

### <a name="2-open-figma-bridge-window"></a>2. Ouvrez la fenêtre de pont Figma

une fois le processus d’importation terminé, vous pouvez trouver Figma bridge sous le menu **> Shared Computer Toolkit > pont Figma**

<img src="images/FigmaToolkit/FigmaBridge_Menu.png" width="500px" alt="Figma Bridge - Menu"><br>

### <a name="3-generate-and-enter-your-figma-token"></a>3. générer et entrer votre jeton Figma

Sur le site Web Figma, cliquez sur le menu Figma dans le coin supérieur gauche, puis ouvrez aide et compte > paramètres du compte. Générez un nouveau jeton d’accès personnel dans la section « jetons d’accès personnels ».

<img src="images/FigmaToolkit/FigmaToolkit_Token.png" width="500px" alt="Figma Bridge - Get Token"><br>

<img src="images/FigmaToolkit/FigmaBridge_Token.png" width="500px" alt="Figma Bridge - Enter Token"><br>


### <a name="4-enter-id-for-a-figma-document"></a>4. Entrez l’ID d’un document Figma
Chaque document Figma a un ID unique dans l’URL. Copiez et collez cet ID dans Figma Bridge.

<img src="images/FigmaToolkit/FigmaToolkit_DocID.png" alt="Figma Bridge - Doc ID"><br>

Cliquez sur le **fichier d’extraction** pour télécharger le fichier Figma. Vous pouvez télécharger d’autres fichiers Figma en entrant un nouvel ID.

Cliquez sur **charger le fichier** pour ouvrir un fichier Figma.

<img src="images/FigmaToolkit/FigmaBridge_Files.png" width="500px" alt="Figma Bridge - Files"><br>

### <a name="5-build-a-page"></a>5. créer une page

Figma Bridge affiche la liste des pages dans le fichier Figma. Vérifiez les pages que vous souhaitez créer dans Unity. Cliquez sur le bouton **générer des pages** .

<img src="images/FigmaToolkit/FigmaBridge_Pages.png" width="500px" alt="Figma Bridge - Pages"><br>

<img src="images/FigmaToolkit/FigmaBridge_Result.png" alt="Figma Bridge - Result"><br>

### <a name="6-refresh-a-document-for-changes"></a>6. actualisation d’un document en vue d’une modification

Vous pouvez modifier le fichier Figma sur le Web (ou à l’aide de l’éditeur de bureau), puis cliquer sur **Actualiser** pour récupérer les modifications. Cliquez sur **générer des pages** à générer avec les mises à jour. De cette façon, vous pouvez facilement itérer votre conception dans Figma et la voir dans Unity.



## <a name="see-also"></a>Voir aussi
* [Toolkit Figma](figma-toolkit.md)
* [Curseurs](cursors.md)
* [Rayon émanant de la main](point-and-commit.md)
* [Button](button.md)
* [Objet avec interaction possible](interactable-object.md)
* [Rectangle englobant et barre de l’application](app-bar-and-bounding-box.md)
* [Manipulation](direct-manipulation.md)
* [Menu de la main](hand-menu.md)
* [Menu proche](near-menu.md)
* [Collection d’objets](object-collection.md)
* [Commande vocale](voice-input.md)
* [Clavier](keyboard.md)
* [Info-bulle](tooltip.md)
* [Tablette](slate.md)
* [Curseur](slider.md)
* [Nuanceur](shader.md)
* [Billboarding et tag-along](billboarding-and-tag-along.md)
* [Affichage de la progression](progress.md)
* [Aimantation de surface](surface-magnetism.md)
