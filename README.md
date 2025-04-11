# Key.file

<<<< 
<<gh pr checkout PULL-REQUEST>>


git fetch origin pull/ID/head: BRANCH_NAME
Switch to the new branch that's based on this pull request:

[main] $ git switch BRANCH_NAME
> Switched to a new branch 'BRANCH_NAME'
At this point, you can do anything you want with this branch. You can run some local tests, or merge other branches into the branch.

When you're ready, you can push the new branch up:

[pull-inactive-pull-request] $ git push origin BRANCH_NAME
> Counting objects: 32, done.
> Delta compression using up to 8 threads.
> Compressing objects: 100 % (26/26), done.
> Writing objects: 100 % (29/29), 74.94 KiB | 0 bytes/s, done.
> Total 29 (delta 8), reused 0 (delta 0)
> To https: // github.com/USERNAME/REPOSITORY.git
> * [new branch]      BRANCH_NAME -> BRANCH_NAME>>

error:

! [remote rejected] HEAD -> refs/pull/1/head(deny updating a hidden ref)
error: failed to push some refs to 'git@github.local:USERNAME/REPOSITORY.git'>>

gh pr create subcommand.

gh pr create
To assign a pull request to an individual, use the - -assignee or -a flags. You can use @ me to self-assign the pull request.

gh pr create - -assignee "@octocat"
To specify the branch into which you want the pull request merged, use the - -base or -B flags. To specify the branch that contains commits for your pull request, use the - -head or -H flags.

gh pr create - -base my-base-branch - -head my-changed-branch
To include a title and body for the new pull request, use the - -title and --body flags.

gh pr create - -title "The bug is fixed" - -body "Everything works again"
To mark a pull request as a draft, use the - -draft flag.

gh pr create - -draft
To add a labels or milestones to the new pull request, use the - -label and --milestone flags.

gh pr create - -label "bug,help wanted" - -milestone octocat-milestone
To add the new pull request to a specific project, use the - -project flag.

gh pr create - -project octocat-project
To assign an individual or team as reviewers, use the - -reviewer flag.

gh pr create - -reviewer monalisa, hubot - -reviewer myorg/team-name
To create the pull request in your default web browser, use the - -web flag.

gh pr create - -web>>

<<file:

"features": {
    "ghcr.io/devcontainers/features/github-cli:1": {}
}>>

$ gh at verify - R cli/cli gh_2.62.0_macOS_arm64.zip
Loaded digest sha256: fdb77f31b8a6dd23c3fd858758d692a45f7fc76383e37d475bdcae038df92afc for file: // gh_2.62.0_macOS_arm64.zip
Loaded 1 attestation from GitHub API
✓ Verification succeeded!

sha256: fdb77f31b8a6dd23c3fd858758d692a45f7fc76383e37d475bdcae038df92afc was attested by:
REPO     PREDICATE_TYPE                  WORKFLOW
cli/cli  https: // slsa.dev/provenance/v1  .github/workflows/deployment.yml@refs/heads/trunk>>
<<$ git clone https: // github.com/sigstore/cosign
$ cd cosign
$ go install ./cmd/cosign
$ $(go env GOPATH)/bin/cosign>>

<< < FROM ghcr.io/sigstore/cosign/cosign: v2.4.1 as cosign-bin

# Source: https://github.com/chainguard-images/static
FROM cgr.dev/chainguard/static: latest
COPY - -from = cosign-bin / ko-app/cosign / usr/local/bin/cosign
ENTRYPOINT["cosign"]
Quick Start
This shows how to:

sign a container image with the default identity-based "keyless signing" method(see the documentation for more information)
verify the container image
Sign a container and store the signature in the registry

Note that you should always sign images based on their digest(@sha256: ...) rather than a tag(: latest) because otherwise you might sign something you didn't intend to!

cosign sign

Generating ephemeral keys...
Retrieving signed certificate...

Note that there may be personally identifiable information associated with this signed artifact.
This may include the email address associated with the account with which you authenticate.
This information will be used for signing this artifact and will be stored in public transparency logs and cannot be removed later.

By typing 'y', you attest that you grant (or have permission to grant) and agree to have this information stored permanently in transparency logs.
Are you sure you would like to continue ? [y/N] y
Your browser will now be opened to:
https: // oauth2.sigstore.dev/auth/auth?access_type = online & client_id = sigstore & code_challenge = OrXitVKUZm2lEWHVt1oQWR4HZvn0rSlKhLcltglYxCY & code_challenge_method = S256 & nonce = 2KvOWeTFxYfxyzHtssvlIXmY6Jk & redirect_uri = http % 3A % 2F % 2Flocalhost % 3A57102 % 2Fauth % 2Fcallback & response_type = code & scope = openid+email & state = 2KvOWfbQJ1caqScgjwibzK2qJmb
Successfully verified SCT...
tlog entry created with index: 12086900
Pushing signature to: >>>>

<< < certificate-identity and --certificate-oidc-issuer flags:

cosign verify - -certificate-identity = --certificate-oidc-issuer =
You can also pass in a regex for the certificate identity and issuer flags, --certificate-identity-regexp and --certificate-oidc-issuer-regexp.

Verify a container against a public key

This command returns 0 if at least one cosign formatted signature for the image is found matching the public key. See the detailed usage below for information and caveats on other signature formats.

Any valid payloads are printed to stdout, in json format. Note that these signed payloads include the digest of the container image, which is how we can be sure these "detached" signatures cover the correct image.

$ cosign verify - -key cosign.pub: 1h
The following checks were performed on these signatures:
    - The cosign claims were validated
    - The signatures were verified against the specified public key
{"Critical": {"Identity": {"docker-reference": ""}, "Image": {"Docker-manifest-digest":
                                                              "sha256:87ef60f558bad79beea6425a3b28989f01dd417164150ab3baab98dcbf04def8"}, "Type": "cosign container image signature"}, "Optional": null}
Verify a container in an air-gapped environment >> >

<< < cosign save(note, this step must be done with a network connection):

cosign initialize  # This will pull in the latest TUF root
cosign save - -dir ./path/to/dir
Now, in an air-gapped environment, this local image can be verified:

cosign verify - -certificate-identity - -certificate-oidc-issuer - -offline - -local-image ./path/to/dir
You'll need to pass in expected values for and to correctly verify this image. If you signed with a keypair, the same command will work, assuming the public key material is present locally:

cosign verify - -key cosign.pub - -offline - -local-image ./path/to/dir >> >

<< << cosign upload blob:

$ echo "my first artifact" > artifact
$ BLOB_SUM =$(shasum - a 256 artifact | cut - d' ' - f 1) & & echo ""
c69d72c98b55258f9026f984e4656f0e9fd3ef024ea3fac1d7e5c7e6249f1626
$ BLOB_NAME = my-artifact -$(uuidgen | head - c 8 | tr 'A-Z' 'a-z')
$ BLOB_URI = ttl.sh /: 1h

$ BLOB_URI_DIGEST =$(cosign upload blob - f artifact) & & echo ""
Uploading file from [artifact] to[ttl.sh/my-artifact-f42c22e0:5m] with media type[text/plain]
File[artifact] is available directly at[ttl.sh/v2/my-artifact-f42c22e0/blobs/sha256:c69d72c98b55258f9026f984e4656f0e9fd3ef024ea3fac1d7e5c7e6249f1626]
Uploaded image to:
ttl.sh/my-artifact-f42c22e0@sha256: 790d47850411e902aabebc3a684eeb78fcae853d4dd6e1cc554d70db7f05f99f
Your users can download it from the "direct" url with standard tools like curl or wget:

$ curl - L ttl.sh/v2//blobs/sha256: > artifact-fetched
The digest is baked right into the URL, so they can check that as well:

$ cat artifact-fetched | shasum - a 256
c69d72c98b55258f9026f984e4656f0e9fd3ef024ea3fac1d7e5c7e6249f1626 -
You can sign it with the normal cosign sign command and flags:

$ cosign sign - -key cosign.key
Enter password for private key:
Pushing signature to: ttl.sh/my-artifact-f42c22e0 >> >> >

<< < brew install tektoncd-cli
Use released tarball

# Get the tar.xz
curl - LO https: // github.com/tektoncd/cli/releases/download/v0.40.0/tkn_0.40.0_Darwin_all.tar.gz
# Extract tkn to your PATH (e.g. /usr/local/bin)
sudo tar xvzf tkn_0.40.0_Darwin_all.tar.gz - C / usr/local/bin tkn >> >> >


<<zypper in ninja>>>>


<<<<<   <<www/
â”œâ”€â”€ build/
â”‚   â”œâ”€â”€ assets/
â”‚   â”‚   â”œâ”€â”€ logo.png
â”‚   â”‚   â””â”€â”€ scenery/
â”‚   â”‚       â”œâ”€â”€ beach.png
â”‚   â”‚       â””â”€â”€ sunset.png
â”‚   â””â”€â”€ other-assets/
â”‚       â””â”€â”€ font.tiff
â””â”€â”€ ...>>
<<zypper in ninja>>

<<apk add ninja>>




<<xbps-install -S ninja>>

<<<brew install ninja
MacPorts:
port install ninja
FreeBSD

pkg install ninja>>>


<<<<conda install -c conda-forge ninja
Pip:
python -m pip install ninja
Spack:
spack install ninja>>>>>
<<<    $ git clone https://github.com/ninja-build/ninja.git && cd ninja
    $ git checkout release>>>

<<<vcvarsall.bat with the appropriate environment.
Build ninja and test it.
The steps for a Visual Studio 2015 64-bit build are outlined here:

    > "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" x64
    > python configure.py --bootstrap
    > ninja --help
Copy the ninja executable to another location, if desired, e.g. C:\local\Ninja.

Finally add the path where ninja.exe is to the PATH variable.

Adjusting build flags

Build in "debug" mode while developing (disables optimizations and builds way faster on Windows):

./configure.py --debug
To use clang, set CXX:

CXX=clang++ ./configure.py>>>>

<<./ninja ninja_test && ./ninja_test --gtest_filter=MyTest.Name>>

<<path/to/misc/measure.py path/to/my/ninja chrome>>

<<<Use /// for doxygen.
Use \a to refer to arguments.
It's not necessary to document each argument, especially when they're relatively self-evident (e.g. in CanonicalizePath(string* path, string* err), the arguments are hopefully obvious)
Building the manual

sudo apt-get install asciidoc --no-install-recommends
./ninja manual
Building the code documentation

sudo apt-get install doxygen
./ninja doxygen>>>



<<<<Install mingw, msys, and python
In the mingw shell, put Python in your path, and python configure.py --bootstrap
To reconfigure, run python configure.py
Remember to strip the resulting executable if size matters to you
Via mingw on Linux (not well supported)

Setup on Ubuntu Lucid:

sudo apt-get install gcc-mingw32 wine
export CC=i586-mingw32msvc-cc CXX=i586-mingw32msvc-c++ AR=i586-mingw32msvc-ar
Setup on Ubuntu Precise:

sudo apt-get install gcc-mingw-w64-i686 g++-mingw-w64-i686 wine
export CC=i686-w64-mingw32-gcc CXX=i686-w64-mingw32-g++ AR=i686-w64-mingw32-ar
Setup on Arch:

Uncomment the [multilib] section of /etc/pacman.conf and sudo pacman -Sy.
sudo pacman -S mingw-w64-gcc wine
export CC=x86_64-w64-mingw32-cc CXX=x86_64-w64-mingw32-c++ AR=x86_64-w64-mingw32-ar
export CFLAGS=-I/usr/x86_64-w64-mingw32/include
Then run:

./configure.py --platform=mingw --host=linux
Build ninja.exe using a Linux ninja binary: /path/to/linux/ninja
Run: ./ninja.exe (implicitly runs through wine(!))
Using Microsoft compilers on Linux (extremely flaky)

The trick is to install just the compilers, and not all of Visual Studio, by following these instructions.

Using gcov

Do a clean debug build with the right flags:

CFLAGS=-coverage LDFLAGS=-coverage ./configure.py --debug
ninja -t clean ninja_test && ninja ninja_test
Run the test binary to generate .gcda and .gcno files in the build directory, then run gcov on the .o files to generate .gcov files in the root directory:

./ninja_test
gcov build/*.o
Look at the generated .gcov files directly, or use your favorite gcov viewer.

Using afl-fuzz

Build with afl-clang++:

CXX=path/to/afl-1.20b/afl-clang++ ./configure.py
ninja
Then run afl-fuzz like so:

afl-fuzz -i misc/afl-fuzz -o /tmp/afl-fuzz-out ./ninja -n -f @@
You can pass -x misc/afl-fuzz-tokens to use the token dictionary. In my testing, that did not seem more effective though.

Using afl-fuzz with asan

If you want to use asan (the isysroot bit is only needed on OS X; if clang can't find C++ standard headers make sure your LLVM checkout includes a libc++ checkout and has libc++ installed in the build directory):

CFLAGS="-fsanitize=address -isysroot $(xcrun -show-sdk-path)" \
    LDFLAGS=-fsanitize=address CXX=path/to/afl-1.20b/afl-clang++ \
    ./configure.py
AFL_CXX=path/to/clang++ ninja
Make sure ninja can find the asan runtime:

DYLD_LIBRARY_PATH=path/to//lib/clang/3.7.0/lib/darwin/ \
    afl-fuzz -i misc/afl-fuzz -o /tmp/afl-fuzz-out ./ninja -n -f @@
>>>>>










using <getAssetPath> the assets in the directory structure above are resolved relative to <build/> <path>

<<import { getAssetPath } from '@stencil/core';

// with an asset base path of "/build/":

// '/build/assets/logo.png'
getAssetPath('assets/logo.png');
// '/build/assets/scenery/beach.png'
getAssetPath('assets/scenery/beach.png');
// '/build/other-assets/font.tiff'
getAssetPath('other-assets/font.tiff'); >>

<<src/
â””â”€â”€ components/
    â”œâ”€â”€ assets/
    â”‚   â”œâ”€â”€ beach.jpg
    â”‚   â””â”€â”€ sunset.jpg
    â””â”€â”€ my-component.tsx>>

<my-component> component will correctly load the assets based on it's <image>

<<// file: my-component.tsx
// 1. getAssetPath is imported from '@stencil/core'
import { Component, Prop, getAssetPath, h } from '@stencil/core';

@Component({
  tag: 'my-component',
  // 2. assetsDirs lists the 'assets' directory as a relative
  //    (sibling) directory
  assetsDirs: ['assets']
})
export class MyComponent {

  @Prop() image = "sunset.jpg";

  render() {
    // 3. the asset path is retrieved relative to the asset 
    //    base path to use in the <img> tag
    const imageSrc = getAssetPath(`./assets/`);
    return <img src={imageSrc} />
  }
}>>

<src>

<<import { Config } from '@stencil/core';

export const config: Config = {
  namespace: 'your-component-library',
  outputTargets: [
    {
      type: 'dist-custom-elements',
      copy: [
        {
          src: '**/*.{jpg,png}',
          dest: 'dist/components/assets',
          warn: true,
        }
      ]
    },
  ], 
  // ...
};>>

<<import { Config } from '@stencil/core';
import copy from 'rollup-plugin-copy';

export const config: Config = {
    namespace: 'copy',
    outputTargets: [
      {
        type: 'dist-custom-elements',
      },
    ],
    rollupPlugins: {
      after: [
        copy({
          targets: [
            {
              src: 'src/**/*.{jpg,png}',
              dest: 'dist/components/assets',
            },
          ],
        }),
      ]
    }
};>>

<</** 
 * Builds a URL to an asset. This is achieved by combining the 
 * provided `path` argument with the base asset path.
 * @param path the path of the asset to build a URL to
 * @returns the built URL
 */
declare function getAssetPath(path: string): string;>>

<<import { getAssetPath } from '@stencil/core';

// with an asset base path of "/build/":
// "/build/"
getAssetPath('');
// "/build/my-image.png"
getAssetPath('my-image.png');
// "/build/assets/my-image.png"
getAssetPath('assets/my-image.png');
// "/build/assets/my-image.png"
getAssetPath('./assets/my-image.png');
// "/assets/my-image.png"
getAssetPath('../assets/my-image.png');
// "/assets/my-image.png"
getAssetPath('/assets/my-image.png');>>

<</**
 * Set the base asset path for resolving components
 * @param path the base asset path
 * @returns the new base asset path
 */
export declare function setAssetPath(path: string): string;>>

<<export { setAssetPath } from '@stencil/core';>>


Now your users can import it directly from your component library, e.g.:

<<import { setAssetPath } from 'my-component-library';
setAssetPath(`//assets./`);>>


Alternatively, one may use document.currentScript.src when working in the browser and not using modules or environment variables (e.g. <document.env.ASSET_PATH)>



<<npm install @trimble-oss/modus-web-components --save>>

<<yarn global add lerna>>
<<# From your top-most-directory/, initialize a workspace
lerna init

# install dependencies
yarn install

# install typescript and node types
yarn add typescript @types/node --dev>>



<<top-most-directory/
â””â”€â”€ packages
    â”œâ”€â”€ stencil-library/
    â”‚   â”œâ”€â”€ stencil.config.js
    â”‚   â””â”€â”€ src/components
    â””â”€â”€ angular-workspace/
        â””â”€â”€ projects/
            â””â”€â”€ component-library/
                â””â”€â”€ src/
                    â”œâ”€â”€ lib/
                    â””â”€â”€ public-api.ts>>



<<yarn create stencil components stencil-library
cd stencil-library
# Install dependencies
yarn install>>


<<npx -p @angular/cli ng new angular-workspace --no-create-application
cd angular-workspace
npx -p @angular/cli ng generate library component-library>>

<<// packages/angular-workspace/projects/component-library/package.json

"peerDependencies": {
   "@angular/common": "^15.1.0",
-  "@angular/core": "^15.1.0"
+  "@angular/core": "^15.1.0",
+  "stencil-library": "*"
}>>

<<# from `/packages/angular-workspace`
yarn remove jasmine-core @types/jasmine>>

<<# Install dependency
yarn add @stencil/angular-output-target --dev>>

<<import { angularOutputTarget } from '@stencil/angular-output-target';

export const config: Config = {
  namespace: 'stencil-library',
  outputTargets: [
    // By default, the generated proxy components will
    // leverage the output from the `dist` target, so we
    // need to explicitly define that output alongside the
    // Angular target
    {
      type: 'dist',
    },
    angularOutputTarget({
      componentCorePackage: 'stencil-library',
      outputType: 'component',
      directivesProxyFile: '../angular-workspace/projects/component-library/src/lib/stencil-generated/components.ts',
      directivesArrayFile: '../angular-workspace/projects/component-library/src/lib/stencil-generated/index.ts',
    }),
  ],
};>>

<<# Build the library and wrappers
yarn build>>

<<import { DIRECTIVES } from './stencil-generated';

@NgModule({
  declarations: [...DIRECTIVES],
  exports: [...DIRECTIVES],
})
export class ComponentLibraryModule {}>>

<<export * from './lib/component-library.module';
export { DIRECTIVES } from './lib/stencil-generated';
export * from './lib/stencil-generated/components';>>

<<import { APP_INITIALIZER, NgModule } from '@angular/core';
import { defineCustomElements } from 'stencil-library/loader';

@NgModule({
  ...,
  providers: [
    {
      provide: APP_INITIALIZER,
      useFactory: () => defineCustomElements,
      multi: true
    },
  ]
})
export class ComponentLibraryModule {}>>

<<# Link the working directory
yarn link>>

From your Angular component library's directory, run the following command:


<Yarn>

<<# Link the package name
yarn link name-of-your-stencil-package>>

<<npx -p @angular/cli ng generate app my-app --standalone=false>>

<<â–² [WARNING] The glob pattern import("./**/.entry.js") did not match any files [empty-glob]

node_modules/@stencil/core/internal/client/index.js:3808:2:
  3808 â”‚   `./.entry.js boolean;
  disabled?: boolean;
  id: string;
  label: string;
 >>

<<  <modus-radio-group checked-id="1" name="my-group"></modus-radio-group>

<script>
  const modusRadioGroup = document.querySelector('modus-radio-group');
  modusRadioGroup.radioButtons = [
    {
      id: '0',
      label: 'Radio 1',
    },
    {
      id: '1',
      checked: true,
      label: 'Radio 2',
    },
    {
      id: '2',
      label: 'Radio 3',
    },
  ];
</script> >>

<<import Form from `@trimbleinc/modus-react-bootstrap/Form>>

<<Form.Check#
import Form.Check from `@trimbleinc/modus-react-bootstrap/Form.Check>>

<< <FormCheck>
  <FormCheck.Input isInvalid type={radio} />
  <FormCheck.Label>Allow us to contact you?</FormCheck.Label>
  <Feedback type="invalid">Yo this is required</Feedback>
</FormCheck> >>

<<FormCheck.Input#
import FormCheck.Input from `@trimbleinc/modus-react-bootstrap/FormCheck.Input`
>>
^'radio'^ ^'checklist'^




<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css?family=Open+Sans:300,400,600,700&display=fallback" rel="stylesheet" />

<<import { defineCustomElements } from '@trimble-oss/modus-web-components/loader';

defineCustomElements();>>

<< <modus-alert message="You've installed Modus Web Components!" type="success" /> >>
<<vscode.html-custom-data.json>>

<<{
  "html.customData": ["./node_modules/@trimble-oss/modus-web-components/dist/vscode.html-custom-data.json"]
}>>
<<npm ci>>

<<npm run build>>

<<npm publish --access public>>

<<npm publish --access public --ignore-scripts --@trimble-oss:registry='https://npm.pkg.github.com'>>

<<{
  "name": "modus-web-components",
  "version": "0.0.0",
  "private": true,
  "description": "Modus Web Components Monorepo",
  "homepage": "https://modus-web-components.trimble.com/",
  "bugs": {
    "url": "https://github.com/trimble-oss/modus-web-components/issues/"
  },
  "repository": {
    "type": "git",
    "url": "git+https://github.com/trimble-oss/modus-web-components.git"
  },
  "license": "MIT",
  "author": "Trimble Inc",
  "scripts": {
    "lint-links": "npx linkinator https://modus-web-components.trimble.com/ --recurse",
    "prettier": "npx prettier --write \"**/*.yml\"",
    "spellcheck": "npx cspell \"**/*.{html,json,md,mdx,toml,ts,yml}\" --no-progress",
    "build-angular": "cd angular-workspace/ng15 && npm i && npm run build && cd ../ng16 && npm i && npm run build && cd ../ng17 && npm i && npm run build && cd ../ng18 && npm i && npm run build",
    "update-mwc-deps": "cd angular-workspace/ng15/projects/trimble-oss/modus-angular-components && npx npm-check-updates -u --dep peer @trimble-oss* && npm i && cd ../../../../ng16/projects/trimble-oss/modus-angular-components && npx npm-check-updates -u --dep peer @trimble-oss* && npm i && cd ../../../../ng17/projects/trimble-oss/modus-angular-components && npx npm-check-updates -u --dep peer @trimble-oss* && npm i && cd ../../../../ng18/projects/trimble-oss/modus-angular-components && npx npm-check-updates -u --dep peer @trimble-oss* && npm i && cd ../../../../../react-workspace/react-17 && npx npm-check-updates -u @trimble-oss* && npm i && cd ../react-18 && npx npm-check-updates -u @trimble-oss* && npm i"
  },
  "engines": {
    "node": ">=18"
  },
  "volta": {
    "node": "18.20.5"
  }
}>>
<<wss-unified-agent.config>>

<<top-most-directory/
â””â”€â”€ packages
    â”œâ”€â”€ stencil-library/
    â”‚   â”œâ”€â”€ stencil.config.js
    â”‚   â””â”€â”€ src/components
    â””â”€â”€ angular-workspace/
        â””â”€â”€ projects/
            â””â”€â”€ component-library/
                â””â”€â”€ src/
                    â”œâ”€â”€ lib/
                    â””â”€â”€ public-api.ts>>



<<NgModule>>

<<import { ComponentLibraryModule } from 'component-library';

@NgModule({
  imports: [ComponentLibraryModule],
})
export class AppModule {}>>

<declarations> and <exports> arrays

<<import { MyComponent } from 'component-library';

@NgModule({
  declarations: [MyComponent],
  exports: [MyComponent],
})
export class AppModule {}>>

<< <my-component first="Your" last="Name"></my-component> >>

<workspace> <(/packages/angular-workspace)> run <npm start> and navigate to <localhost:4200>

<<npx -p @angular/cli ng generate app my-app>>
<<npx -p @angular/cli ng build component-library>>

<<â–² [WARNING] The glob pattern import("./**/.entry.js") did not match any files [empty-glob]

node_modules/@stencil/core/internal/client/index.js:3808:2:
  3808 â”‚   `./.entry.js from '@angular/core';
import { ComponentLibraryModule } from 'component-library';

@Component({
  selector: 'app-root',
  standalone: true,
  imports: [ComponentLibraryModule],
  templateUrl: './app.component.html',
})
export class AppComponent {}>>

<< <my-component first="Your" last="Name"></my-component> >>

<<yarn create stencil component my-component-lib>>


<componentCorePackage> would be set to:

<<stencil.config.ts
export const config: Config = {
  ...,
  outputTargets: [
    angularOutputTarget({
      componentCorePackage: 'my-component-lib',
      // ... additional config options
    })
  ]
}>>


Which would result in an import path like:

<<import { MyComponent } from 'my-component-lib/components/my-component.js';>>

<<const angularValueAccessorBindings: ValueAccessorConfig[] = [
  {
    elementSelectors: ['my-input[type=text]'],
    event: 'myChange',
    targetAttr: 'value',
    type: 'text',
  },
];

export const config: Config = {
  namespace: 'stencil-library',
  outputTargets: [
    angularOutputTarget({
      componentCorePackage: 'component-library',
      directivesProxyFile: '{path to your proxy file}',
      valueAccessorConfigs: angularValueAccessorBindings,
    }),
    {
      type: 'dist',
      esmLoaderPath: '../loader',
    },
  ],
};>>


<<createNodeLogger(process: any): Logger>>

<<createNodeSystem(process: any): CompilerSystem>>

<< run(init: CliInitOptions): Promise<void> >>

<< runTask(process: any, config: Config, task: TaskCommand,  sys?: CompilerSystem): Promise<void> >>

<@stencil/core/compiler/stencil.js.> This module can work in a NodeJS environment.

<<// NodeJS (commonjs)
const stencil = require('@stencil/core/compiler');>>


<<transpile()
transpile(code: string, opts?: TranspileOptions): Promise<TranspileResults> >>


The <transpile()> function inputs source code as a string, with various options within the second argument. The function is stateless and returns a <Promise> of the results, including diagnostics and the transpiled code. The <transpile()> function does not handle any bundling, minifying, or precompiling any CSS preprocessing like Sass or Less.

The <transpileSync()> equivalent is available so the same function it can be called synchronously. However, TypeScript must be already loaded within the global for it to work, where as the async transpile() function will load TypeScript automatically.

Since TypeScript is used, the source code will transpile from TypeScript to JavaScript, and does not require Babel presets. Additionally, the results includes an imports array of all the <import> paths found in the source file. The transpile options can be used to set the <module> format, such as <cjs> and <JavaScript> target version, such as <es2017>

<<transpileSync()
transpileSync(code: string, opts?: TranspileOptions): TranspileResults>>

<< createCompiler(config: Config): Promise<Compiler> >>


<stencil build>
<Compiler> instance. The config provided should already be created using the <loadConfig({...})>

<<import { createNodeLogger, createNodeSys } from '@stencil/core/sys/node';
import { createCompiler, loadConfig } from '@stencil/core/compiler';

const logger = createNodeLogger(process);
const sys = createNodeSys(process);
const validated = await loadConfig({
  logger,
  sys,
  config: {
    /* user config */
  },
});
const compiler = await createCompiler(validated.config);
const results = await compiler.build();>>

<<createSystem(): CompilerSystem>>

The compiler uses a <CompilerSystem>


<<www/
â”œâ”€â”€ build/
â”‚   â”œâ”€â”€ assets/
â”‚   â”‚   â”œâ”€â”€ logo.png
â”‚   â”‚   â””â”€â”€ scenery/
â”‚   â”‚       â”œâ”€â”€ beach.png
â”‚   â”‚       â””â”€â”€ sunset.png
â”‚   â””â”€â”€ other-assets/
â”‚       â””â”€â”€ font.tiff
â””â”€â”€ ...>>

<< <html>
  <head>
    <script src="https://cdn.jsdelivr.net/npm/my-component-library/dist/my-component-library.js"></script>
    <script type="module">
      import { setAssetPath } from 'https://cdn.jsdelivr.net/npm/my-component-library/dist/my-component-library.js';
      setAssetPath(`/`);
    </script>
  </head>
  <body>
    <ion-toggle></ion-toggle>
  </body>
</html> >>

<< <script type="module" src="https://unpkg.com/my-design-system"></script> >>


or by importing it in the bootstrap script of your application:

<<import 'my-design-system';>>

To ensure that the right entry file is loaded when importing the project, define the following fields in your package.json:

<<{
  "exports": "./dist/esm/my-design-system.js",
  "main": "./dist/cjs/my-design-system.js",
  "unpkg": "dist/my-design-system/my-design-system.esm.js",
}>>

<<export function someUtilFunction() {
  console.log('do stuff');
}


src/components/my-cmp.tsx
import { someUtilFunction } from '../utils.ts';

@Component({
  tag: 'my-cmp'
})
export class MyCmp {}


src/components/my-cmp-two.tsx
import { someUtilFunction } from '../utils.ts';

@Component({
  tag: 'my-cmp-two'
})
export class MyCmpTwo {}>>
>>>>>

<<<gh codespace code
>>

<<gh codespace code --web
>>

<<<gh codespace jupyter
€>>>

<<gh codespace ssh
>>

<<<"features": {
    "ghcr.io/devcontainers/features/python:1": {}
}<>>>

<<<ms-python.python
ms-python.vscode-pylance
ms-python.autopep8
OS Support>>>



This Feature should work on recent versions of Debian/Ubuntu, RedHat Enterprise Linux, Fedora, Alma, and RockyLinux distributions with the apt, yum, dnf, or microdnf package manager installed.

bash is required to execute the <<<install.sh>>>



<<<<Breadcrumbs
{ "id": "python", "version": "1.7.1", "name": "Python", "documentationURL": "https://github.com/devcontainers/features/tree/main/src/python", "description": "Installs the provided version of Python, as well as PIPX, and other common Python utilities. JupyterLab is conditionally installed with the python feature. Note: May require source code compilation.", "options": { "version": { "type": "string", "proposals": [ "latest", "os-provided", "none", "3.12", "3.11", "3.10", "3.9", "3.8", "3.7", "3.6" ], "default": "os-provided", "description": "Select a Python version to install." }, "installTools": { "type": "boolean", "default": true, "description": "Flag indicating whether or not to install the tools specified via the 'toolsToInstall' option. Default is 'true'." }, "toolsToInstall": { "type": "string", "default": "flake8,autopep8,black,yapf,mypy,pydocstyle,pycodestyle,bandit,pipenv,virtualenv,pytest,pylint", "description": "Comma-separated list of tools to install when 'installTools' is true. Defaults to a set of common Python tools like pylint." }, "optimize": { "type": "boolean", "default": false, "description": "Optimize Python for performance when compiled (slow)" }, "enableShared": { "type": "boolean", "default": false, "description": "Enable building a shared Python library" }, "installPath": { "type": "string", "default": "/usr/local/python", "description": "The path where python will be installed." }, "installJupyterlab": { "type": "boolean", "default": false, "description": "Install JupyterLab, a web-based interactive development environment for notebooks" }, "configureJupyterlabAllowOrigin": { "type": "string", "default": "", "description": "Configure JupyterLab to accept HTTP requests from the specified origin" }, "httpProxy": { "type": "string", "default": "", "description": "Connect to GPG keyservers using a proxy for fetching source code signatures by configuring this option" } }, "containerEnv": { "PYTHON_PATH": "/usr/local/python/current", "PIPX_HOME": "/usr/local/py-utils", "PIPX_BIN_DIR": "/usr/local/py-utils/bin", "PATH": "/usr/local/python/current/bin:/usr/local/py-utils/bin:/usr/local/jupyter:${PATH}" }, "customizations": { "vscode": { "extensions": [ "ms-python.python", "ms-python.vscode-pylance", "ms-python.autopep8" ], "settings": { "github.copilot.chat.codeGeneration.instructions": [ { "text": "This dev container includes `python3` and `pip3` pre-installed and available on the `PATH`, along with the Python language extensions for Python development." } ], "python.defaultInterpreterPath": "/usr/local/python/current/bin/python", "[python]": { "editor.defaultFormatter": "ms-python.autopep8" } } } }, "installsAfter": [ "ghcr.io/devcontainers/features/common-utils", "ghcr.io/devcontainers/features/oryx" ] }>>>>


From: Keith Bieszczat mibnumber001k@gmail.com
Date: Sun, 16 Mar 2025 00:51:00 -0500
Subject: [PATCH] Create AuthenticatedCARD.md
MIME-Version: 1.0
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: 8bit
<<<<PATH>>>>
<<Cancel.
GET_CONFIRMATION description>>
<<use this for token inputs: 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>>
<<PRESET_PASSPHRASE [--inquire] <string_or_keygrip> <timeout> [<hexstring>]>>
<<HAVEKEY keygrips>>
<<smartcard
LEARN [--send]
This command is used to register a smartcard. With the --send option given the certificates are sent back.>>
<<GETEVENTCOUNTER
This>>
<< gpg-connect-agent --dirmngr 'loadswdb --force' /bye
--keyserver name
Use name as your keyserver. This is the server that gpg communicates with to receive keys, send keys, and search for keys. The format of the name is a URI: â€˜scheme:[//]keyservername[:port]â€™ The scheme is the type of keyserver: "hkp" for the HTTP (or compatible) keyservers or "ldap" for the LDAP keyservers. Note that your particular installation of GnuPG may have other keyserver types available as well. Keyserver schemes are case-insensitive. After the keyserver name, optional keyserver configuration options may be provided. These are the same as the --keyserver-options of gpg, but apply only to this particular keyserver.
Some keyservers synchronize with each other, so there is not always a need to send keys to more than one server. Some keyservers use round robin DNS to give a different keyserver each time you use it.
If exactly two keyservers are configured and only one is a Tor hidden service (.onion), Dirmngr selects the keyserver to use depending on whether Tor is locally running or not. The check for a running Tor is done for each new connection.
If no keyserver is explicitly configured, dirmngr will use the built-in default of https://keyserver.ubuntu.com. To avoid the use of a default keyserver the value none can be used.
Windows users with a keyserver running on their Active Directory may use the short form ldap:/// for name to access this directory.
For accessing anonymous LDAP keyservers name is in general just a ldaps://ldap.example.com. A BaseDN parameter should never be specified. If authentication is required things are more complicated and two methods are available:
The modern method (since version 2.2.28) is to use the very same syntax as used with the option --ldapserver. Please see over there for details; here is an example:

   keyserver ldap:ldap.example.com::uid=USERNAME,ou=GnuPG Users,
   dc=example,dc=com:PASSWORD::starttls
The other method is to use a full URL for name; for example:

   keyserver ldaps://ldap.example.com/????bindname=uid=USERNAME
   %2Cou=GnuPG%20Users%2Cdc=example%2Cdc=com,password=PASSWORD
Put>>
<<<System
These System root certificates are used by: FIXME
The origin of the system provided certificates depends on the platform. On Windows all certificates from the Windows System Stores ROOT and CA are used.
On other platforms the certificates are read from the first file found form this list: /etc/ssl/ca-bundle.pem, /etc/ssl/certs/ca-certificates.crt, /etc/pki/tls/cert.pem, /usr/local/share/certs/ca-root-nss.crt, /etc/ssl/cert.pem.
GnuPG
The GnuPG specific certificates stored in the directory /etc/gnupg/trusted-certs are only used to validate CRLs.
OpenPGP keyserver
For accessing the OpenPGP keyservers the only certificates used are those set with the configuration option hkp-cacert.
OpenPGP keyserver pool
This is usually only one certificate read from the file /usr/local/share/gnupg/gnupg/sks-keyservers.netCA.pem. If this certificate exists it is used to access the special keyservers hkps.pool.sks-keyservers.net (or hkps://keys.gnupg.net).
Please note that gpgsm accepts Root CA certificates for its own purposes only if they are listed in its file trustlist.txt. dirmngr does not make use of this list - except FIXME.
To be able to see diagnostics it is often useful to put at least the following lines into the configuration file ~/gnupg/dirmngr.conf:
log-file ~/dirmngr.log
verbose
You may want to check the log file to see whether all desired root CA certificates are correctly loaded.
To be able to perform OCSP requests you probably want to add the line:
allow-ocsp
To make sure that new options are read or that after the installation of a new GnuPG versions the right dirmngr version is running, you should kill an existing dirmngr so that a new instance is started as needed by the other components:
gpgconf --kill dirmngr
Direct interfaction with the dirmngr is possible by using the command
gpg-connect-agent --dirmngr>>>
<<SIGHUP
This signal flushes all internally cached CRLs as well as any cached certificates. Then the certificate cache is reinitialized as on startup. Options are re-read from the configuration file. Instead of sending this signal it is better to use
gpgconf --reload dirmngr
SIGTERM
Shuts down the process but waits until all current requests are fulfilled. If the process has received 3 of these signals and requests are still pending, a shutdown is forced. You may also use
gpgconf --kill dirmngr
instead of this signal
SIGINT
Shuts down the process immediately.
SIGUSR1>>
<<API.
gpg-connect-agent --dirmngr 'keyserver --hosttable' /bye
To inhibit the use of a particular host you have noticed in one of the keyserver pools, you may use
gpg-connect-agent --dirmngr 'keyserver --dead pgpkeys.bnd.de' /bye
The description of the keyserver command can be printed using
gpg-connect-agent --dirmngr 'help keyserver' /bye>>
<<3.6.1 Return the certificate(s) found
Lookup certificate. To allow multiple patterns (which are ORed) quoting is required: Spaces are to be translated into "+" or into "%20"; obviously this requires that the usual escape quoting rules are applied. The server responds with:
S: D <DER encoded certificate>
S: END
S: D <second DER encoded certificate>
S: END
S: OK
In this example 2 certificates are returned. The server may return any number of certificates; OK will also be returned when no certificates were found. The dirmngr might return a status line
S: S TRUNCATED <n>
To indicate that the output was truncated to N items due to a limitation of the server or by an arbitrary set limit.
The option --url may be used if instead of a search pattern a complete URL to the certificate is known:
C: LOOKUP --url CN%3DWerner%20Koch,o%3DIntevation%20GmbH,c%3DDE?userCertificate
If the option --cache-only is given, no external lookup is done so that only certificates from the cache are returned.
With the option --single, the first and only the first match will be returned. Unless option --cache-only is also used, no local lookup will be done in this case.>>>
<<ISVALID [--only-ocsp] [--force-default-responder] certid|certfpr>>
<< S: INQUIRE SENDCERT <CertID>
C: D <DER encoded certificate>
C: END
A client should be aware that DirMngr may ask for more than one certificate.
If Dirmngr has a certificate but the signature of the certificate could not been validated because the root certificate is not known to dirmngr as trusted, it may ask back to see whether the client trusts this the root certificate:
S: INQUIRE ISTRUSTED <CertHexfpr>
C: D 1
C: END>>
<<
Check whether the certificate with FINGERPRINT (SHA-1 hash of the entire X.509 certificate blob) is valid or not by consulting the CRL responsible for this certificate. If the fingerprint has not been given or the certificate is not known, the function inquires the certificate using:
S: INQUIRE TARGETCERT
C: D <DER encoded certificate>
C: END
Thus the caller is expected to return the certificate for the request (which should match FINGERPRINT) as a binary blob. Processing then takes place without further interaction; in particular dirmngr tries to locate other required certificate by its own mechanism which includes a local certificate store as well as a list of trusted root certificates.
The return code is 0 for success; i.e. the certificate has not been revoked or one of the usual error codes from libgpg-error.>>
<<OCSP
CHECKOCSP [--force-default-responder] [fingerprint]
Check whether the certificate with fingerprint (the SHA-1 hash of the entire X.509 certificate blob) is valid by consulting the appropriate OCSP responder. If the fingerprint has not been given or the certificate is not known by Dirmngr, the function inquires the certificate using:
S: INQUIRE TARGETCERT
C: D <DER encoded certificate>
C: END
Thus the caller is expected to return the certificate for the request (which should match fingerprint) as a binary blob. Processing then takes place without further interaction; in particular dirmngr tries to locate other required certificates by its own mechanism which includes a local certificate store as well as a list of trusted root certificates.
If the option --force-default-responder is given, only the default OCSP responder is used. This option is the per-command variant of the global option --ignore-ocsp-service-url.>>
<<using>>
<<S: INQUIRE TARGETCERT
C: D <DER encoded certificate>
C: END>>
<<using
S: INQUIRE TARGETCERT
C: D <DER encoded certificate>
C: END>>
<<command>> <--edit-key>>
<<$ export GNUPGHOME="$(mktemp -d)"
\$ cat >foo <<EOF
%echo Generating a basic OpenPGP key
Key-Type: DSA
Key-Length: 1024
Subkey-Type: ELG-E
Subkey-Length: 1024
Name-Real: Joe Tester
Name-Comment: with stupid passphrase
Name-Email: joe@foo.bar
Expire-Date: 0
Passphrase: abc
# Do a commit here, so that we can later print "done" :-)
%commit
%echo done
EOF
\$ gpg --batch --generate-key foo
[...]
\$ gpg --list-secret-keys
/tmp/tmp.0NQxB74PEf/pubring.kbx
sec dsa1024 2016-12-16 [SCA]
768E895903FC1C44045C8CB95EEBDB71E9E849D0
uid [ultimate] Joe Tester (with stupid passphrase) joe@foo.bar
ssb elg1024 2016-12-16 [E]
If you want to create a key with the default algorithms you would use these parameters:

 %echo Generating a default key
 Key-Type: default
 Subkey-Type: default
 Name-Real: Joe Tester
 Name-Comment: with stupid passphrase
 Name-Email: joe@foo.bar
 Expire-Date: 0
 Passphrase: abc
 # Do a commit here, so that we can later print "done" :-)
 %commit
 %echo done>>
<<GENKEY
GPGSM checks whether this command is allowed and then does an INQUIRY to get the key parameters, the client should then send the key parameters in the native format:

S: INQUIRE KEY_PARAM native
C: D foo:fgfgfg
C: D bar
C: END>>
<<command:
LISTKEYS pattern
is used. To allow multiple patterns (which are ORed during the search) quoting is required: Spaces are to be translated into "+" or into "%20"; in turn this requires that the usual escape quoting rules are done.
LISTSECRETKEYS pattern
Lists only the keys where a secret key is available.
The list commands are affected by the option
OPTION list-mode=mode>>
<<EXPORT [--data [--armor] [--base64]] [--] pattern>>
<<IMPORT [--re-import]>>
<<YUBIKEY cmd args
Various commands pertaining to Yubikey tokens with cmd being:
LIST
List supported and enabled Yubikey applications.
ENABLE usb|nfc|all [otp|u2f|opgp|piv|oath|fido2|all]
DISABLE
Enable or disable the specified or all applications on the given interface.
The support for OpenPGP cards in gpg-card is not yet complete. For missing features, please continue to use gpg --card-edit.
GnuPG has support for PIV cards (â€œPersonal Identity Verificationâ€ as specified by NIST Special Publication 800-73-4). This section describes how to initialize (personalize) a fresh Yubikey token featuring the PIV application (requires Yubikey-5). We assume that the credentials have not yet been changed and thus are:
Authentication key
This is a 24 byte key described by the hex string
010203040506070801020304050607080102030405060708.
PIV Application PIN
This is the string 123456.
PIN Unblocking Key
This is the string 12345678.
See the example section on how to change these defaults. For production use it is important to use secure values for them. Note that the Authentication Key is not queried via the usual Pinentry dialog but needs to be entered manually or read from a file. The use of a dedicated machine to personalize tokens is strongly suggested.
To see what is on the card, the command list can be given. We will use the interactive mode in the following (the string gpg/card> is the prompt). An example output for a fresh card is:
gpg/card> list
Reader ...........: 1050:0407:X:0
Card type ........: yubikey
Card firmware ....: 5.1.2
Serial number ....: D2760001240102010006090746250000
Application type .: OpenPGP
Version ..........: 2.1
[...]
It can be seen by the â€œApplication typeâ€ line that GnuPG selected the OpenPGP application of the Yubikey. This is because GnuPG assigns the highest priority to the OpenPGP application. To use the PIV application of the Yubikey several methods can be used:
With a Yubikey 5 or later the OpenPGP application on the Yubikey can be disabled:
gpg/card> yubikey disable all opgp
gpg/card> yubikey list
Application USB NFC
OTP yes yes
U2F yes yes
OPGP no no
PIV yes no
OATH yes yes
FIDO2 yes yes
gpg/card> reset
The reset is required so that the GnuPG system rereads the card. Note that disabled applications keep all their data and can at any time be re-enabled (use help yubikey).
Another option, which works for all Yubikey versions, is to disable the support for OpenPGP cards in scdaemon. This is done by adding the line
disable-application openpgp
to ~/.gnupg/scdaemon.conf and by restarting scdaemon, either by killing the process or by using gpgconf --kill scdaemon. Finally the default order in which card applications are tried by scdaemon can be changed. For example to prefer PIV over OpenPGP it is sufficient to add
application-priority piv
to ~/.gnupg/scdaemon.conf and to restart scdaemon. This has an effect only on tokens which support both, PIV and OpenPGP, but does not hamper the use of OpenPGP only tokens.
With one of these methods employed the list command of gpg-card shows this:
gpg/card> list
Reader ...........: 1050:0407:X:0
Card type ........: yubikey
Card firmware ....: 5.1.2
Serial number ....: FF020001008A77C1
Application type .: PIV
Version ..........: 1.0
Displayed s/n ....: yk-9074625
PIN usage policy .: app-pin
PIN retry counter : - 3 -
PIV authentication: [none]
keyref .....: PIV.9A
Card authenticat. : [none]
keyref .....: PIV.9E
Digital signature : [none]
keyref .....: PIV.9C
Key management ...: [none]
keyref .....: PIV.9D
In case several tokens are plugged into the computer, gpg-card will show only one. To show another token the number of the token (0, 1, 2, ...) can be given as an argument to the list command. The command list --cards prints a list of all inserted tokens.
Note that the â€œDisplayed s/nâ€ is printed on the token and also shown in Pinentry prompts asking for the PIN. The four standard key slots are always shown, if other key slots are initialized they are shown as well. The PIV authentication key (internal reference PIV.9A) is used to authenticate the card and the card holder. The use of the associated private key is protected by the Application PIN which needs to be provided once and the key can the be used until the card is reset or removed from the reader or USB port. GnuPG uses this key with its Secure Shell support. The Card authentication key (PIV.9E) is also known as the CAK and used to support physical access applications. The private key is not protected by a PIN and can thus immediately be used. The Digital signature key (PIV.9C) is used to digitally sign documents. The use of the associated private key is protected by the Application PIN which needs to be provided for each signing operation. The Key management key (PIV.9D) is used for encryption. The use of the associated private key is protected by the Application PIN which needs to be provided only once so that decryption operations can then be done until the card is reset or removed from the reader or USB port.
We now generate three of the four keys. Note that GnuPG does currently not use the the Card authentication key; however, that key is mandatory by the PIV standard and thus we create it too. Key generation requires that we authenticate to the card. This can be done either on the command line (which would reveal the key):
gpg/card> auth 010203040506070801020304050607080102030405060708
or by reading the key from a file. That file needs to consist of one LF terminated line with the hex encoded key (as above):
gpg/card> auth < myauth.key
As usual â€˜help authâ€™ gives help for this command. An error message is printed if a non-matching key is used. The authentication is valid until a reset of the card or until the card is removed from the reader or the USB port. Note that that in non-interactive mode the â€˜<â€™ needs to be quoted so that the shell does not interpret it as a its own redirection symbol.
Here are the actual commands to generate the keys:
gpg/card> generate --algo=nistp384 PIV.9A
PIV card no. yk-9074625 detected
gpg/card> generate --algo=nistp256 PIV.9E
PIV card no. yk-9074625 detected
gpg/card> generate --algo=rsa2048 PIV.9C
PIV card no. yk-9074625 detected
If a key has already been created for one of the slots an error will be printed; to create a new key anyway the option â€˜--forceâ€™ can be used. Note that only the private and public keys have been created but no certificates are stored in the key slots. In fact, GnuPG uses its own non-standard method to store just the public key in place of the the certificate. Other application will not be able to make use these keys until gpgsm or another tool has been used to create and store the respective certificates. Let us see what the list command now shows:
gpg/card> list
Reader ...........: 1050:0407:X:0
Card type ........: yubikey
Card firmware ....: 5.1.2
Serial number ....: FF020001008A77C1
Application type .: PIV
Version ..........: 1.0
Displayed s/n ....: yk-9074625
PIN usage policy .: app-pin
PIN retry counter : - 3 -
PIV authentication: 213D1825FDE0F8240CB4E4229F01AF90AC658C2E
keyref .....: PIV.9A (auth)
algorithm ..: nistp384
Card authenticat. : 7A53E6CFFE7220A0E646B4632EE29E5A7104499C
keyref .....: PIV.9E (auth)
algorithm ..: nistp256
Digital signature : 32A6C6FAFCB8421878608AAB452D5470DD3223ED
keyref .....: PIV.9C (sign,cert)
algorithm ..: rsa2048
Key management ...: [none]
keyref .....: PIV.9D
The primary information for each key is the keygrip, a 40 byte hex-string identifying the key. This keygrip is a unique identifier for the specific parameters of a key. It is used by gpg-agent and other parts of GnuPG to associate a private key to its protocol specific certificate format (X.509, OpenPGP, or SecureShell). Below the keygrip the key reference along with the key usage capabilities are show. Finally the algorithm is printed in the format used by gpg. At that point no other information is shown because for these new keys gpg wonâ€™t be able to find matching certificates.
Although we could have created the Key management key also with the generate command, we will create that key off-card so that a backup exists. To accomplish this a key needs to be created with either gpg or gpgsm or imported in one of these tools. In our example we create a self-signed X.509 certificate (exit the gpg-card tool, first):
\$ gpgsm --gen-key -o encr.crt
(1) RSA
(2) Existing key
(3) Existing key from card
Your selection? 1
What keysize do you want? (3072) 2048
Requested keysize is 2048 bits
Possible actions for a RSA key:
(1) sign, encrypt
(2) sign
(3) encrypt
Your selection? 3
Enter the X.509 subject name: CN=Encryption key for yk-9074625,O=example,C=DE
Enter email addresses (end with an empty line):
otto@example.net
Enter DNS names (optional; end with an empty line):
 
Enter URIs (optional; end with an empty line):
 
Create self-signed certificate? (y/N) y
These parameters are used:
Key-Type: RSA
Key-Length: 2048
Key-Usage: encrypt
Serial: random
Name-DN: CN=Encryption key for yk-9074625,O=example,C=DE
Name-Email: otto@example.net
Proceed with creation? (y/N)
Now creating self-signed certificate. This may take a while ...
gpgsm: about to sign the certificate for key: &34798AAFE0A7565088101CC4AE31C5C8C74461CB
gpgsm: certificate created
Ready.
\$ gpgsm --import encr.crt
gpgsm: certificate imported
gpgsm: total number processed: 1
gpgsm: imported: 1
Note the last step which imported the created certificate. If you you instead created a certificate signing request (CSR) instead of a self-signed certificate and sent this off to a CA you would do the same import step with the certificate received from the CA. Take note of the keygrip (prefixed with an ampersand) as shown during the certificate creation or listed it again using â€˜gpgsm --with-keygrip -k otto@example.netâ€™. Now to move the key and certificate to the card start gpg-card again and enter:
gpg/card> writekey PIV.9D 34798AAFE0A7565088101CC4AE31C5C8C74461CB
gpg/card> writecert PIV.9D < encr.crt
If you entered a passphrase to protect the private key, you will be asked for it via the Pinentry prompt. On success the key and the certificate has been written to the card and a list command shows:
[...]
Key management ...: 34798AAFE0A7565088101CC4AE31C5C8C74461CB
keyref .....: PIV.9D (encr)
algorithm ..: rsa2048
used for ...: X.509
user id ..: CN=Encryption key for yk-9074625,O=example,C=DE
user id ..: otto@example.net
In case the same key (identified by the keygrip) has been used for several certificates you will see several â€œused forâ€ parts. With this the encryption key is now fully functional and can be used to decrypt messages encrypted to this certificate. TAKE CARE: the original key is still stored on-disk and should be moved to a backup medium. This can simply be done by copying the file 34798AAFE0A7565088101CC4AE31C5C8C74461CB.key from the directory ~/.gnupg/private-keys-v1.d/ to the backup medium and deleting the file at its original place.
The final example is to create a self-signed certificate for digital signatures. Leave gpg-card using quit or by pressing Control-D and use gpgsm:
\$ gpgsm --learn
\$ gpgsm --gen-key -o sign.crt
Please select what kind of key you want:
(1) RSA
(2) Existing key
(3) Existing key from card
Your selection? 3
Serial number of the card: FF020001008A77C1
Available keys:
(1) 213D1825FDE0F8240CB4E4229F01AF90AC658C2E PIV.9A nistp384
(2) 7A53E6CFFE7220A0E646B4632EE29E5A7104499C PIV.9E nistp256
(3) 32A6C6FAFCB8421878608AAB452D5470DD3223ED PIV.9C rsa2048
(4) 34798AAFE0A7565088101CC4AE31C5C8C74461CB PIV.9D rsa2048
Your selection? 3
Possible actions for a RSA key:
(1) sign, encrypt
(2) sign
(3) encrypt
Your selection? 2
Enter the X.509 subject name: CN=Signing key for yk-9074625,O=example,C=DE
Enter email addresses (end with an empty line):
otto@example.net
Enter DNS names (optional; end with an empty line):
 
Enter URIs (optional; end with an empty line):
 
Create self-signed certificate? (y/N)
These parameters are used:
Key-Type: card:PIV.9C
Key-Length: 1024
Key-Usage: sign
Serial: random
Name-DN: CN=Signing key for yk-9074625,O=example,C=DE
Name-Email: otto@example.net
Proceed with creation? (y/N) y
Now creating self-signed certificate. This may take a while ...
gpgsm: about to sign the certificate for key: &32A6C6FAFCB8421878608AAB452D5470DD3223ED
gpgsm: certificate created
Ready.
\$ gpgsm --import sign.crt
gpgsm: certificate imported
gpgsm: total number processed: 1
gpgsm: imported: 1
The use of â€˜gpgsm --learnâ€™ is currently necessary so that gpg-agent knows what keys are available on the card. The need for this command will eventually be removed. The remaining commands are similar to the creation of an on-disk key. However, here we select the â€˜Digital signatureâ€™ key. During the creation process you will be asked for the Application PIN of the card. The final step is to write the certificate to the card using gpg-card:
gpg/card> writecert PIV.9C < sign.crt
By running list again we will see the fully initialized card:
Reader ...........: 1050:0407:X:0
Card type ........: yubikey
Card firmware ....: 5.1.2
Serial number ....: FF020001008A77C1
Application type .: PIV
Version ..........: 1.0
Displayed s/n ....: yk-9074625
PIN usage policy .: app-pin
PIN retry counter : - [verified] -
PIV authentication: 213D1825FDE0F8240CB4E4229F01AF90AC658C2E
keyref .....: PIV.9A (auth)
algorithm ..: nistp384
Card authenticat. : 7A53E6CFFE7220A0E646B4632EE29E5A7104499C
keyref .....: PIV.9E (auth)
algorithm ..: nistp256
Digital signature : 32A6C6FAFCB8421878608AAB452D5470DD3223ED
keyref .....: PIV.9C (sign,cert)
algorithm ..: rsa2048
used for ...: X.509
user id ..: CN=Signing key for yk-9074625,O=example,C=DE
user id ..: otto@example.net
Key management ...: 34798AAFE0A7565088101CC4AE31C5C8C74461CB
keyref .....: PIV.9D (encr)
algorithm ..: rsa2048
used for ...: X.509
user id ..: CN=Encryption key for yk-9074625,O=example,C=DE
user id ..: otto@example.net
It is now possible to sign and to encrypt with this card using gpgsm and to use the â€˜PIV authenticationâ€™ key with ssh:
\$ ssh-add -l
384 SHA256:0qnJ0Y0ehWxKcx2frLfEljf6GCdlO55OZed5HqGHsaU cardno:yk-9074625 (ECDSA)
As usual use ssh-add with the uppercase â€˜-Lâ€™ to list the public ssh key. To use the certificates with Thunderbird or Mozilla, please consult the Scute manual for details.
If you want to use the same PIV keys also for OpenPGP (for example on a Yubikey to avoid switching between OpenPGP and PIV), this is also possible:
\$ gpgsm --learn
\$ gpg --full-gen-key
Please select what kind of key you want:
(1) RSA and RSA (default)
(2) DSA and Elgamal
(3) DSA (sign only)
(4) RSA (sign only)
(14) Existing key from card
Your selection? 14
Serial number of the card: FF020001008A77C1
Available keys:
(1) 213D1825FDE0F8240CB4E4229F01AF90AC658C2E PIV.9A nistp384 (auth)
(2) 7A53E6CFFE7220A0E646B4632EE29E5A7104499C PIV.9E nistp256 (auth)
(3) 32A6C6FAFCB8421878608AAB452D5470DD3223ED PIV.9C rsa2048 (cert,sign)
(4) 34798AAFE0A7565088101CC4AE31C5C8C74461CB PIV.9D rsa2048 (encr)
Your selection? 3
Please specify how long the key should be valid.
0 = key does not expire
<n> = key expires in n days
<n>w = key expires in n weeks
<n>m = key expires in n months
<n>y = key expires in n years
Key is valid for? (0)
Key does not expire at all
Is this correct? (y/N) y
GnuPG needs to construct a user ID to identify your key.
Real name:
Email address: otto@example.net
Comment:
You selected this USER-ID:
"otto@example.net"
Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? o
gpg: key C3AFA9ED971BB365 marked as ultimately trusted
gpg: revocation certificate stored as '[...]D971BB365.rev'
public and secret key created and signed.
Note that this key cannot be used for encryption. You may want to use
the command "--edit-key" to generate a subkey for this purpose.
pub rsa2048 2019-04-04 [SC]
7F899AE2FB73159DD68A1B20C3AFA9ED971BB365
uid otto@example.net
Note that you will be asked two times to enter the PIN of your PIV card. If you run gpg in --expert mode you will also ge given the option to change the usage flags of the key. The next typescript shows how to add the encryption subkey:
\$ gpg --edit-key 7F899AE2FB73159DD68A1B20C3AFA9ED971BB365
Secret key is available.
sec rsa2048/C3AFA9ED971BB365
created: 2019-04-04 expires: never usage: SC
card-no: FF020001008A77C1
trust: ultimate validity: ultimate
[ultimate] (1). otto@example.net
gpg> addkey
Secret parts of primary key are stored on-card.
Please select what kind of key you want:
(3) DSA (sign only)
(4) RSA (sign only)
(5) Elgamal (encrypt only)
(6) RSA (encrypt only)
(14) Existing key from card
Your selection? 14
Serial number of the card: FF020001008A77C1
Available keys:
(1) 213D1825FDE0F8240CB4E4229F01AF90AC658C2E PIV.9A nistp384 (auth)
(2) 7A53E6CFFE7220A0E646B4632EE29E5A7104499C PIV.9E nistp256 (auth)
(3) 32A6C6FAFCB8421878608AAB452D5470DD3223ED PIV.9C rsa2048 (cert,sign)
(4) 34798AAFE0A7565088101CC4AE31C5C8C74461CB PIV.9D rsa2048 (encr)
Your selection? 4
Please specify how long the key should be valid.
0 = key does not expire
<n> = key expires in n days
<n>w = key expires in n weeks
<n>m = key expires in n months
<n>y = key expires in n years
Key is valid for? (0)
Key does not expire at all
Is this correct? (y/N) y
Really create? (y/N) y
sec rsa2048/C3AFA9ED971BB365
created: 2019-04-04 expires: never usage: SC
card-no: FF020001008A77C1
trust: ultimate validity: ultimate
ssb rsa2048/7067860A98FCE6E1
created: 2019-04-04 expires: never usage: E
card-no: FF020001008A77C1
[ultimate] (1). otto@example.net
gpg> save>>
<<query {
viewer {
login
}
}>>
<<array.
{
"data": null,
"errors": [
{
"message": "Objects must have selections (field 'nodes' returns Repository but has no selections)",
"locations": [
{
"line": 5,
"column": 8
}
]
}
]
}
It's possible you might run into an unexpected error that is not related to the schema. If this happens, the message will include a reference code you can use when reporting the issue:
{
"data": null,
"errors": [
{
"message": "Something went wrong while executing your query. This is most likely a GitHub bug. Please include \"7571:3FF6:552G94B:69F45B7:5913BBEQ\" when reporting this issue."
}
]
}>>
<<Here's a contrived example of a schema that defines interface X and object Y:
interface X {
some_field: String!
other_field: String!
}
type Y implements X {
some_field: String!
other_field: String!
new_field: String!
}>>
<<Query __schema to list all types defined in the schema and get details about each:
query {
__schema {
types {
name
kind
description
fields {
name
}
}
}
}
Query __type to get details about any type:
query {
__type(name: "Repository") {
name
kind
description
fields {
name
}
}
}
You can also run an introspection query of the schema via a GET request:
curl -H "Authorization: bearer TOKEN" https://api.github.com/graphql
Note
If you get the response "message": "Bad credentials" or 401 Unauthorized, check that you are using a valid token. If you receive a 403 error with Resource not accessible by personal access token, ensure that your fine-grained personal access token is targeted to the correct resource owner. For example, it must target the organization that owns the repository you are trying to access.
The results are in JSON, so we recommend pretty-printing them for easier reading and searching. You can use a command-line tool like jq or pipe the results into python -m json.tool for this purpose.
Alternatively, you can pass the idl media type to return the results in IDL format, which is a condensed version of the schema:
\$ curl -H "Authorization: bearer TOKEN" -H "Accept: application/vnd.github.v4.idl" \
https://api.github.com/graphql>>
<<curl -i --header "Authorization: Bearer YOUR-TOKEN" https://api.github.com/user
you'll get a response that includes the node_id of the authenticated user:
{
"login": "octocat",
"id": 1,
"avatar_url": "https://github.com/images/error/octocat_happy.gif",
"gravatar_id": "",
"url": "https://api.github.com/users/octocat",
"html_url": "octocat - Overview ",
"followers_url": "https://api.github.com/users/octocat/followers",
"following_url": "https://api.github.com/users/octocat/following{/other_user}",
"gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
"starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
"subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
"organizations_url": "https://api.github.com/users/octocat/orgs",
"repos_url": "https://api.github.com/users/octocat/repos",
"events_url": "https://api.github.com/users/octocat/events{/privacy}",
"received_events_url": "https://api.github.com/users/octocat/received_events",
"type": "User",
"site_admin": false,
"name": "monalisa octocat",
"company": "GitHub",
"blog": "https://github.com/blog",
"location": "San Francisco",
"email": "octocat@github.com",
"hireable": false,
"bio": "There once was...",
"public_repos": 2,
"public_gists": 1,
"followers": 20,
"following": 0,
"created_at": "2008-01-14T04:33:35Z",
"updated_at": "2008-01-14T04:33:35Z",
"private_gists": 81,
"total_private_repos": 100,
"owned_private_repos": 100,
"disk_usage": 10000,
"collaborators": 8,
"two_factor_authentication": true,
"plan": {
"name": "Medium",
"space": 400,
"private_repos": 20,
"collaborators": 0
},
"node_id": "MDQ6VXNlcjU4MzIzMQ=="
}
2. Find the object type in GraphQL
In this example, the node_id value is MDQ6VXNlcjU4MzIzMQ==. You can use this value to query the same object in GraphQL.
You'll need to know the object's type first, though. You can check the type with a simple GraphQL query:
query {
node(id:"MDQ6VXNlcjU4MzIzMQ==") {
__typename
}
}
This type of queryâ€”that is, finding the node by IDâ€”is known as a "direct node lookup."
When you run this query, you'll see that the __typename is User.
Do a direct node lookup in GraphQL
Once you've confirmed the type, you can use an inline fragment to access the object by its ID and return additional data. In this example, we define the fields on User that we'd like to query:
query {
node(id:"MDQ6VXNlcjU4MzIzMQ==") {
... on User {
name
login
}
}
}>>>
<token:##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##>
<<curl -L \
-H "Accept: application/vnd.github+json" \
-H "Authorization: Bearer <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>" \
-H "X-GitHub-Api-Version: 2022-11-28" \
https://api.github.com/user
<<curl -L \
-X PATCH \
-H "Accept: application/vnd.github+json" \
-H "Authorization: Bearer <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>" \
-H "X-GitHub-Api-Version: 2022-11-28" \
https://api.github.com/user \
-d '{"blog":"https://github.com/blog","name":"monalisa octocat"}'>>
<<http://api.github.com >> with your enterprise's dedicated subdomain at <<api.SUBDOMAIN.ghe.com>>
<<name: Context testing
on: push
jobs:
dump_contexts_to_log:
runs-on: ubuntu-latest
steps:
- name: Dump GitHub context
env:
GITHUB_CONTEXT: ${{ toJson(github) }}
run: echo "$GITHUB_CONTEXT"
- name: Dump job context
env:
JOB_CONTEXT: ${{ toJson(job) }}
run: echo "$JOB_CONTEXT"
- name: Dump steps context
env:
STEPS_CONTEXT: ${{ toJson(steps) }}
run: echo "$STEPS_CONTEXT"
- name: Dump runner context
env:
RUNNER_CONTEXT: ${{ toJson(runner) }}
run: echo "$RUNNER_CONTEXT"
- name: Dump strategy context
env:
STRATEGY_CONTEXT: ${{ toJson(strategy) }}
run: echo "$STRATEGY_CONTEXT"
- name: Dump matrix context
env:
MATRIX_CONTEXT: ${{ toJson(matrix) }}
run: echo "$MATRIX_CONTEXT"
jobs:
use_api:
runs-on: ubuntu-latest
permissions: {}
steps:
- env:
GH_TOKEN: ${{ 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 }}
run: |
curl --request GET \
--url "https://api.github.com/PATH " \
--header "Authorization: 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"
<curl> <<GITHUB_TOKEN>> as an environment variable, and use the <run> keyword to execute the GitHub CLI <api> subcommand. For more information about the run keyword, see Workflow syntax for GitHub Actions.
In the following example workflow, replace PATH with the path of the endpoint. For more information about the path, see Getting started with the REST API.
<<jobs:
use_api:
runs-on: ubuntu-latest
permissions: {}
steps:
- env:
GH_TOKEN: ${{ ##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## }}
run: |
gh api /PATH>>
<<$ sudo ufw enable>>
<<$ man programs_name>>
<<$ sudo dnf install certbot python3-certbot-apache>>
<<$ sudo certbot --apache>>
<<$ sudo certbot renew --dry-run
Now, to automate the renewal of the certificate by the script, edit the crontab.
\$ crontab -e
Specify the cron job shown and save the changes.
0 * * * * /usr/sbin/certbot-auto renew>>
<<gpg --full-generate-key>>
If you are not on version 2.1.17 or greater, the gpg --full-generate-key command doesn't work. Paste the text below and skip to step 6.
<Shell>
<<terminal>>
<# cat file.txt>
<<example>>
<<<<# cat file1.txt file2.txt file3.txt>>>>>
<<ssh -T git@github.com in the terminal:
\$ ssh -T git@github.com
Attempt to SSH in to github
Hi USERNAME! You've successfully authenticated, but GitHub does not provide
shell access.>>
<<ssh -T git@github.com once more. If all is well, you'll get back the same prompt as you did locally.
If you're unsure if your local key is being used, you can also inspect the SSH_AUTH_SOCK variable on your server:
\$ echo "$SSH_AUTH_SOCK"
Print out the SSH_AUTH_SOCK variable
/tmp/ssh-4hNGMk8AZX/agent.79453
If the variable is not set, it means that agent forwarding is not working:
\$ echo "$SSH_AUTH_SOCK"
Print out the SSH_AUTH_SOCK variable
[No output]
\$ ssh -T git@github.com
Try to SSH to github
Permission denied (publickey).
Troubleshooting SSH agent forwarding
Here are some things to look out for when troubleshooting SSH agent forwarding.
You must be using an SSH URL to check out code
SSH forwarding only works with SSH URLs, not HTTP(s) URLs. Check the .git/config file on your server and ensure the URL is an SSH-style URL like below:
[remote "origin"]
url = git@github.com:YOUR_ACCOUNT/YOUR_PROJECT.git
fetch = +refs/heads/:refs/remotes/origin/
Your SSH keys must work locally
Before you can make your keys work through agent forwarding, they must work locally first. Our guide on generating SSH keys can help you set up your SSH keys locally.
Your system must allow SSH agent forwarding
Sometimes, system configurations disallow SSH agent forwarding. You can check if a system configuration file is being used by entering the following command in the terminal:
\$ ssh -v URL
Connect to the specified URL with verbose debug output
OpenSSH_8.1p1, LibreSSL 2.7.3
debug1: Reading configuration data /Users/YOU/.ssh/config
debug1: Applying options for example.com
debug1: Reading configuration data /etc/ssh_config
debug1: Applying options for *
\$ exit
Returns to your local command prompt
In the example above, the file ~/.ssh/config is loaded first, then /etc/ssh_config is read. We can inspect that file to see if it's overriding our options by running the following commands:
\$ cat /etc/ssh_config
Print out the /etc/ssh_config file
Host *
SendEnv LANG LC_*
ForwardAgent no
In this example, our /etc/ssh_config file specifically says ForwardAgent no, which is a way to block agent forwarding. Deleting this line from the file should get agent forwarding working once more.
Your server must allow SSH agent forwarding on inbound connections
Agent forwarding may also be blocked on your server. You can check that agent forwarding is permitted by SSHing into the server and running sshd_config. The output from this command should indicate that AllowAgentForwarding is set.
Your local ssh-agent must be running
On most computers, the operating system automatically launches ssh-agent for you. On Windows, however, you need to do this manually. We have a guide on how to start ssh-agent whenever you open Git Bash.
To verify that ssh-agent is running on your computer, type the following command in the terminal:
\$ echo "$SSH_AUTH_SOCK"
Print out the SSH_AUTH_SOCK variable
/tmp/launch-kNSlgU/Listeners
Your key must be available to ssh-agent
You can check that your key is visible to ssh-agent by running the following command:
ssh-add -L
If the command says that no identity is available, you'll need to add your key:
ssh-add YOUR-KEY
Tip
On macOS, ssh-agent will "forget" this key, once it gets restarted during reboots. But you can import your SSH keys into Keychain using this command:
ssh-add --apple-use-keychain YOUR-KEY
Note
The --apple-use-keychain option stores the passphrase in your keychain for you when you add an SSH key to the ssh-agent. If you chose not to add a passphrase to your key, run the command without the --apple-use-keychain option.
The --apple-use-keychain option is in Apple's standard version of ssh-add. In macOS versions prior to Monterey (12.0), the --apple-use-keychain and --apple-load-keychain flags used the syntax -K and -A, respectively.
If you don't have Apple's standard version of ssh-add installed, you may receive an error. For more information, see Error: ssh-add: illegal option -- apple-use-keychain.
If you continue to be prompted for your passphrase, you may need to add the command to your ~/.zshrc file (or your ~/.bashrc file for bash).>>
<<$ ssh-keygen -p -f ~/.ssh/id_ed25519
Enter old passphrase: [Type old passphrase]
Key has comment 'your_email@example.com'
Enter new passphrase (empty for no passphrase): [Type new passphrase]
Enter same passphrase again: [Repeat the new passphrase]
Your identification has been saved with the new passphrase.>>
<<ssh-add command, and not an application installed by macports, homebrew, or some other external source.
Start the ssh-agent in the background.
\$ eval "$(ssh-agent -s)"
Agent pid 59566
Depending on your environment, you may need to use a different command. For example, you may need to use root access by running sudo -s -H before starting the ssh-agent, or you may need to use exec ssh-agent bash or exec ssh-agent zsh to run the ssh-agent.
If you're using macOS Sierra 10.12.2 or later, you will need to modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain.
First, check to see if your ~/.ssh/config file exists in the default location.
\$ open ~/.ssh/config
The file /Users/YOU/.ssh/config does not exist.
If the file doesn't exist, create the file.
touch ~/.ssh/config
Open your ~/.ssh/config file, then modify the file to contain the following lines. If your SSH key file has a different name or path than the example code, modify the filename or path to match your current setup.
Text
Host GitHub · Build and ship software on a single, collaborative platform 
AddKeysToAgent yes
UseKeychain yes
IdentityFile ~/.ssh/id_ed25519
Note
If you chose not to add a passphrase to your key, you should omit the UseKeychain line.
If you see a Bad configuration option: usekeychain error, add an additional line to the configuration's' Host *.github.com section.
Text
Host GitHub · Build and ship software on a single, collaborative platform 
IgnoreUnknown UseKeychain
Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file.
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
Note
The --apple-use-keychain option stores the passphrase in your keychain for you when you add an SSH key to the ssh-agent. If you chose not to add a passphrase to your key, run the command without the --apple-use-keychain option.
The --apple-use-keychain option is in Apple's standard version of ssh-add. In macOS versions prior to Monterey (12.0), the --apple-use-keychain and --apple-load-keychain flags used the syntax -K and -A, respectively.
If you don't have Apple's standard version of ssh-add installed, you may receive an error. For more information, see Error: ssh-add: illegal option -- apple-use-keychain.
If you continue to be prompted for your passphrase, you may need to add the command to your ~/.zshrc file (or your ~/.bashrc file for bash).
Add the SSH public key to your account on GitHub. For more information, see Adding a new SSH key to your GitHub account.
Generating a new SSH key for a hardware security key
If you are using macOS or Linux, you may need to update your SSH client or install a new SSH client prior to generating a new SSH key. For more information, see Error: Unknown key type.
Insert your hardware security key into your computer.
Open Terminal.
Paste the text below, replacing the email address in the example with the email address associated with your GitHub account.
ssh-keygen -t ed25519-sk -C "your_email@example.com"
Note
If the command fails and you receive the error invalid format or feature not supported, you may be using a hardware security key that does not support the Ed25519 algorithm. Enter the following command instead.
ssh-keygen -t ecdsa-sk -C "your_email@example.com"
When you are prompted, touch the button on your hardware security key.
When you are prompted to "Enter a file in which to save the key," press Enter to accept the default file location.
Enter a file in which to save the key (/Users/YOU/.ssh/id_ed25519_sk): [Press enter]
When you are prompted to type a passphrase, press Enter.
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]>>
<<ssh-keygen -t ed25519 -C "mibnumber001k@gmail.com"
Note
If you are using a legacy system that doesn't support the Ed25519 algorithm, use:
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
This creates a new SSH key, using the provided email as a label.
Generating public/private ALGORITHM key pair.
When you're prompted to "Enter a file in which to save the key", you can press Enter to accept the default file location. Please note that if you created SSH keys previously, ssh-keygen may ask you to rewrite another key, in which case we recommend creating a custom-named SSH key. To do so, type the default file location and replace id_ALGORITHM with your custom key name.
Enter a file in which to save the key (/Users/YOU/.ssh/id_ALGORITHM): [Press enter]
At the prompt, type a secure passphrase. For more information, see Working with SSH key passphrases.
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
Adding your SSH key to the ssh-agent
Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key. When adding your SSH key to the agent, use the default macOS ssh-add command, and not an application installed by macports, homebrew, or some other external source.
Start the ssh-agent in the background.
\$ eval "$(ssh-agent -s)"
Agent pid 59566
<<gpg --default-new-key-algo rsa4096 --gen-key>>
<<gpg --list-secret-keys --keyid-format=long>>
<<$ gpg --list-secret-keys --keyid-format=long
/Users/hubot/.gnupg/secring.gpg
sec 4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid Hubot hubot@example.com
ssb 4096R/4BB6D45482678BE3 2016-03-10
<< gpg --armor --export 3AA5C34371567BD2
Prints the GPG key ID, in ASCII armor format>>
<<<--gpg-sign, unset this configuration so the default format of openpgp will be used.
git config --global --unset gpg.format
Use the gpg --list-secret-keys --keyid-format=long command to list the long form of the GPG keys for which you have both a public and private key. A private key is required for signing commits or tags.
Shell
gpg --list-secret-keys --keyid-format=long
Note
Some GPG installations on Linux may require you to use gpg2 --list-keys --keyid-format LONG to view a list of your existing keys instead. In this case you will also need to configure Git to use gpg2 by running git config --global gpg.program gpg2.
From the list of GPG keys, copy the long form of the GPG key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:
Shell
\$ gpg --list-secret-keys --keyid-format=long
/Users/hubot/.gnupg/secring.gpg
sec 4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid Hubot hubot@example.com
ssb 4096R/4BB6D45482678BE3 2016-03-10
To set your primary GPG signing key in Git, paste the text below, substituting in the GPG primary key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:
git config --global user.signingkey 3AA5C34371567BD2
Alternatively, you may want to use a subkey. In this example, the GPG subkey ID is 4BB6D45482678BE3:
git config --global user.signingkey 4BB6D45482678BE3
If you use multiple keys and subkeys, then you should append an exclamation mark ! to the key to tell git that this is your preferred key. Sometimes you may need to escape the exclamation mark with a back slash: \!.
Optionally, to configure Git to sign all commits and tags by default, enter the following command:
git config --global commit.gpgsign true
git config --global tag.gpgSign true
For more information, see Signing commits.
To add your GPG key to your .bashrc startup file, run the following command:
[ -f ~/.bashrc ] && echo -e '\nexport GPG_TTY=$(tty)' >> ~/.bashrc>>>
<< git config --global gpg.format ssh
To set your SSH signing key in Git, paste the text below, substituting /PATH/TO/.SSH/KEY.PUB with the path to the public key you'd like to use.
git config --global user.signingkey /PATH/TO/.SSH/KEY.PUB>>
<< $ cat ~/.ssh/id_ed25519.pub
Then select and copy the contents of the id_ed25519.pub file
displayed in the terminal to your clipboard>>
<<<>>> from cryptography.hazmat.primitives import hashes
pn = dh.DHParameterNumbers(p, g)
parameters = pn.parameters()
peer_public_numbers = dh.DHPublicNumbers(y, pn)
peer_public_key = peer_public_numbers.public_key()>>>
<<<# Key.file
location:%20/home/linuxbrew%0ANote:%20Homebrew%20is%20pre-installed%20on%20image%20but%20not%20added%20to%20PATH.%0Arun%20the%20eval%20%22$(/home/linuxbrew/.linuxbrew/bin/brew%20shellenv)%22%20command%0Ato%20accomplish%20this.
<<<Location: /home/linuxbrew
Note: Homebrew is pre-installed on image but not added to PATH.
run the eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)" command
to accomplish this.>>
<<Both Xdebug and PCOV extensions are installed, but only Xdebug is enabled.>>
<<User: postgres
PostgreSQL service is disabled by default.
Use the following command as a part of your job to start the service: 'sudo systemctl start postgresql.service'>>
<<User: root
Password: root
MySQL service is disabled by default.
Use the following command as a part of your job to start the service: 'sudo systemctl start mysql.service'>>
<<name: Run commands on different operating systems
on:
push:
branches: [ main ]
pull_request:
branches: [ main ]
jobs:
Run-npm-on-Ubuntu:
name: Run npm on Ubuntu
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@v4
- uses: actions/setup-node@v4
with:
node-version: '14'
- run: npm help
Run-PSScriptAnalyzer-on-Windows:
name: Run PSScriptAnalyzer on Windows
runs-on: windows-latest
steps:
- uses: actions/checkout@v4
- name: Install PSScriptAnalyzer module
shell: pwsh
run: |
Set-PSRepository PSGallery -InstallationPolicy Trusted
Install-Module PSScriptAnalyzer -ErrorAction Stop
- name: Get list of rules
shell: pwsh
run: |
Get-ScriptAnalyzerRule
<<name: Build on Ubuntu
on: push
jobs:
build:
runs-on: ubuntu-latest
steps:
- name: Check out repository code
uses: actions/checkout@v4
- name: Install jq tool
run: |
sudo apt-get update
sudo apt-get install jq
Note
Always run sudo apt-get update before installing a package. In case the apt index is stale, this command fetches and re-indexes any available packages, which helps prevent package installation failures.
Installing software on macOS runners
The following example demonstrates how to install Brew packages and casks as part of a job.
name: Build on macOS
on: push
jobs:
build:
runs-on: macos-latest
steps:
- name: Check out repository code
uses: actions/checkout@v4
- name: Install GitHub CLI
run: |
brew update
brew install gh
- name: Install Microsoft Edge
run: |
brew update
brew install --cask microsoft-edge>>>>>>
<<his command:
echo scd getinfo reader_list \
| gpg-connect-agent --decode | awk '/^D/ {print $2}'
--card-timeout n
This option is deprecated. In GnuPG 2.0, it used to be used for DISCONNECT command to control timing issue. Since DISCONNECT command works synchronously, it has no effect.
--enable-pinpad-varlen
Please specify this option when the card reader supports variable length input for pinpad (default is no). For known readers (listed in ccid-driver.c and apdu.c), this option is not needed. Note that if your card reader doesnâ€™t supports variable length input but you want to use it, you need to specify your pinpad request on your card.
--disable-pinpad
Even if a card reader features a pinpad, do not try to use it.
--deny-admin
This option disables the use of admin class commands for card applications where this is supported. Currently we support it for the OpenPGP card. This option is useful to inhibit accidental access to admin class command which could ultimately lock the card through wrong PIN numbers. Note that GnuPG versions older than 2.0.11 featured an --allow-admin option which was required to use such admin commands. This option has no more effect today because the default is now to allow admin commands.
--disable-application name
This option disables the use of the card application named name. This is mainly useful for debugging or if a application with lower priority should be used by default.
--application-priority namelist
This option allows one to change the order in which applications of a card a tried if no specific application was requested. namelist is a space or comma delimited list of application names. Unknown names are simply skipped. Applications not mentioned in the list are put in the former order at the end of the new priority list.
To get the list of current active applications, use

gpg-connect-agent 'scd getinfo app_list' /bye
<<gpg-connect-agent 'help COMMAND' /bye>>
<<used.
GENKEY [--no-protection] [--preset] [<cache_nonce>]
Invokes the key generation process and the server will then inquire on the generation parameters, like:
S: INQUIRE KEYPARM
C: D (genkey (rsa (nbits 1024)))
C: END
The format of the key parameters which depends on the algorithm is of the form:

(genkey
  (algo
    (parameter_name_1 ....)
      ....
    (parameter_name_n ....)))
If everything succeeds, the server returns the public key in a SPKI like S-Expression like this:

 (public-key
   (rsa
 (n <mpi>)
 (e <mpi>)))
Here is an example session:
C: GENKEY
S: INQUIRE KEYPARM
C: D (genkey (rsa (nbits 1024)))
C: END
S: D (public-key
S: D (rsa (n 326487324683264) (e 10001)))
S OK key created
<<2.6.6 Importing a Root Certificate
Actually we do not import a Root Cert but provide a way to validate any piece of data by storing its Hash along with a description and an identifier in the PSE. Here is the interface description:

ISTRUSTED <fingerprint>
Check whether the OpenPGP primary key or the X.509 certificate with the given fingerprint is an ultimately trusted key or a trusted Root CA certificate. The fingerprint should be given as a hexstring (without any blanks or colons or whatever in between) and may be left padded with 00 in case of an MD5 fingerprint. GPGAgent will answer with:

OK
The key is in the table of trusted keys.

ERR 304 (Not Trusted)
The key is not in this table.
Gpg needs the entire list of trusted keys to maintain the web of trust; the following command is therefore quite helpful:

LISTTRUSTED
GpgAgent returns a list of trusted keys line by line:

S: D 000000001234454556565656677878AF2F1ECCFF P
S: D 340387563485634856435645634856438576457A P
S: D FEDC6532453745367FD83474357495743757435D S
S: OK
The first item on a line is the hexified fingerprint where MD5 fingerprints are 00 padded to the left and the second item is a flag to indicate the type of key (so that gpg is able to only take care of PGP keys). P = OpenPGP, S = S/MIME. A client should ignore the rest of the line, so that we can extend the format in the future.
Finally a client should be able to mark a key as trusted:
MARKTRUSTED fingerprint "P"|"S"
The server will then pop up a window to ask the user whether she really trusts this key. For this it will probably ask for a text to be displayed like this:
S: INQUIRE TRUSTDESC
C: D Do you trust the key with the fingerprint @FPR@
C: D bla fasel blurb.
C: END
S: OK>>
<<_gh-Godstimetravelcorporation-e.scpf-foundation-roblox.fandom.com>>
<<595a2d4e38>>
<<
Create a TXT record in your DNS configuration for the following hostname: _gh-Godstimetravelcorporation-e.scpf-foundation-roblox.fandom.com
Use this code for the value of the TXT record: 595a2d4e38. Please note that the code will expire in 7 days.
Wait until your DNS configuration changes. This could take up to 72 hours to propagate.
<<podman pull registry.opensuse.org/kubevirt/cdi-apiserver:1.61.0 podman pull registry.opensuse.org/kubevirt/cdi-apiserver:1.61.0-1.2 podman pull registry.opensuse.org/kubevirt/cdi-apiserver:1.61.0.9.342>> <<podman pull registry.opensuse.org/kubevirt/cdi-apiserver:1.61.0-1.1>> <obs://build.opensuse.org/openSUSE:Factory/containerfile/0aa2e3c4fc8a6a0c87755acabca779b4-cdi-apiserver-container> <<podman pull registry.opensuse.org/kubevirt/cdi-cloner:1.61.0>>
<<<<PATH>>>>
<<query {
viewer {
login
}
}>>
<<array.
{
"data": null,
"errors": [
{
"message": "Objects must have selections (field 'nodes' returns Repository but has no selections)",
"locations": [
{
"line": 5,
"column": 8
}
]
}
]
}
It's possible you might run into an unexpected error that is not related to the schema. If this happens, the message will include a reference code you can use when reporting the issue:
{
"data": null,
"errors": [
{
"message": "Something went wrong while executing your query. This is most likely a GitHub bug. Please include \"7571:3FF6:552G94B:69F45B7:5913BBEQ\" when reporting this issue."
}
]
}>>
<<Here's a contrived example of a schema that defines interface X and object Y:
interface X {
some_field: String!
other_field: String!
}
type Y implements X {
some_field: String!
other_field: String!
new_field: String!
}>>
<<Query __schema to list all types defined in the schema and get details about each:
query {
__schema {
types {
name
kind
description
fields {
name
}
}
}
}
Query __type to get details about any type:
query {
__type(name: "Repository") {
name
kind
description
fields {
name
}
}
}
You can also run an introspection query of the schema via a GET request:
curl -H "Authorization: bearer TOKEN" https://api.github.com/graphql
Note
If you get the response "message": "Bad credentials" or 401 Unauthorized, check that you are using a valid token. If you receive a 403 error with Resource not accessible by personal access token, ensure that your fine-grained personal access token is targeted to the correct resource owner. For example, it must target the organization that owns the repository you are trying to access.
The results are in JSON, so we recommend pretty-printing them for easier reading and searching. You can use a command-line tool like jq or pipe the results into python -m json.tool for this purpose.
Alternatively, you can pass the idl media type to return the results in IDL format, which is a condensed version of the schema:
\$ curl -H "Authorization: bearer TOKEN" -H "Accept: application/vnd.github.v4.idl" \
https://api.github.com/graphql>>
<<curl -i --header "Authorization: Bearer YOUR-TOKEN" https://api.github.com/user
you'll get a response that includes the node_id of the authenticated user:
{
"login": "octocat",
"id": 1,
"avatar_url": "https://github.com/images/error/octocat_happy.gif",
"gravatar_id": "",
"url": "https://api.github.com/users/octocat",
"html_url": "octocat - Overview ",
"followers_url": "https://api.github.com/users/octocat/followers",
"following_url": "https://api.github.com/users/octocat/following{/other_user}",
"gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
"starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
"subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
"organizations_url": "https://api.github.com/users/octocat/orgs",
"repos_url": "https://api.github.com/users/octocat/repos",
"events_url": "https://api.github.com/users/octocat/events{/privacy}",
"received_events_url": "https://api.github.com/users/octocat/received_events",
"type": "User",
"site_admin": false,
"name": "monalisa octocat",
"company": "GitHub",
"blog": "https://github.com/blog",
"location": "San Francisco",
"email": "octocat@github.com",
"hireable": false,
"bio": "There once was...",
"public_repos": 2,
"public_gists": 1,
"followers": 20,
"following": 0,
"created_at": "2008-01-14T04:33:35Z",
"updated_at": "2008-01-14T04:33:35Z",
"private_gists": 81,
"total_private_repos": 100,
"owned_private_repos": 100,
"disk_usage": 10000,
"collaborators": 8,
"two_factor_authentication": true,
"plan": {
"name": "Medium",
"space": 400,
"private_repos": 20,
"collaborators": 0
},
"node_id": "MDQ6VXNlcjU4MzIzMQ=="
}
2. Find the object type in GraphQL
In this example, the node_id value is MDQ6VXNlcjU4MzIzMQ==. You can use this value to query the same object in GraphQL.
You'll need to know the object's type first, though. You can check the type with a simple GraphQL query:
query {
node(id:"MDQ6VXNlcjU4MzIzMQ==") {
__typename
}
}
This type of queryâ€”that is, finding the node by IDâ€”is known as a "direct node lookup."
When you run this query, you'll see that the __typename is User.
Do a direct node lookup in GraphQL
Once you've confirmed the type, you can use an inline fragment to access the object by its ID and return additional data. In this example, we define the fields on User that we'd like to query:
query {
node(id:"MDQ6VXNlcjU4MzIzMQ==") {
... on User {
name
login
}
}
}>>>
<token:##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##>
<<curl -L \
-H "Accept: application/vnd.github+json" \
-H "Authorization: Bearer <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>" \
-H "X-GitHub-Api-Version: 2022-11-28" \
https://api.github.com/user
<<curl -L \
-X PATCH \
-H "Accept: application/vnd.github+json" \
-H "Authorization: Bearer <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>" \
-H "X-GitHub-Api-Version: 2022-11-28" \
https://api.github.com/user \
-d '{"blog":"https://github.com/blog","name":"monalisa octocat"}'>>
<<http://api.github.com >> with your enterprise's dedicated subdomain at <<api.SUBDOMAIN.ghe.com>>
<<name: Context testing
on: push
jobs:
dump_contexts_to_log:
runs-on: ubuntu-latest
steps:
- name: Dump GitHub context
env:
GITHUB_CONTEXT: ${{ toJson(github) }}
run: echo "$GITHUB_CONTEXT"
- name: Dump job context
env:
JOB_CONTEXT: ${{ toJson(job) }}
run: echo "$JOB_CONTEXT"
- name: Dump steps context
env:
STEPS_CONTEXT: ${{ toJson(steps) }}
run: echo "$STEPS_CONTEXT"
- name: Dump runner context
env:
RUNNER_CONTEXT: ${{ toJson(runner) }}
run: echo "$RUNNER_CONTEXT"
- name: Dump strategy context
env:
STRATEGY_CONTEXT: ${{ toJson(strategy) }}
run: echo "$STRATEGY_CONTEXT"
- name: Dump matrix context
env:
MATRIX_CONTEXT: ${{ toJson(matrix) }}
run: echo "$MATRIX_CONTEXT"
jobs:
use_api:
runs-on: ubuntu-latest
permissions: {}
steps:
- env:
GH_TOKEN: ${{ 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 }}
run: |
curl --request GET \
--url "https://api.github.com/PATH " \
--header "Authorization: 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"
<curl> <<GITHUB_TOKEN>> as an environment variable, and use the <run> keyword to execute the GitHub CLI <api> subcommand. For more information about the run keyword, see Workflow syntax for GitHub Actions.
In the following example workflow, replace PATH with the path of the endpoint. For more information about the path, see Getting started with the REST API.
<<jobs:
use_api:
runs-on: ubuntu-latest
permissions: {}
steps:
- env:
GH_TOKEN: ${{ ##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## }}
run: |
gh api /PATH>>
<<$ sudo ufw enable>>
<<$ man programs_name>>
<<$ sudo dnf install certbot python3-certbot-apache>>
<<$ sudo certbot --apache>>
<<$ sudo certbot renew --dry-run
Now, to automate the renewal of the certificate by the script, edit the crontab.
\$ crontab -e
Specify the cron job shown and save the changes.
0 * * * * /usr/sbin/certbot-auto renew>>
<<gpg --full-generate-key>>
If you are not on version 2.1.17 or greater, the gpg --full-generate-key command doesn't work. Paste the text below and skip to step 6.
<Shell>
<<terminal>>
<# cat file.txt>
<<example>>
<<<<# cat file1.txt file2.txt file3.txt>>>>>
<<ssh -T git@github.com in the terminal:
\$ ssh -T git@github.com
Attempt to SSH in to github
Hi USERNAME! You've successfully authenticated, but GitHub does not provide
shell access.>>
<<ssh -T git@github.com once more. If all is well, you'll get back the same prompt as you did locally.
If you're unsure if your local key is being used, you can also inspect the SSH_AUTH_SOCK variable on your server:
\$ echo "$SSH_AUTH_SOCK"
Print out the SSH_AUTH_SOCK variable
/tmp/ssh-4hNGMk8AZX/agent.79453
If the variable is not set, it means that agent forwarding is not working:
\$ echo "$SSH_AUTH_SOCK"
Print out the SSH_AUTH_SOCK variable
[No output]
\$ ssh -T git@github.com
Try to SSH to github
Permission denied (publickey).
Troubleshooting SSH agent forwarding
Here are some things to look out for when troubleshooting SSH agent forwarding.
You must be using an SSH URL to check out code
SSH forwarding only works with SSH URLs, not HTTP(s) URLs. Check the .git/config file on your server and ensure the URL is an SSH-style URL like below:
[remote "origin"]
url = git@github.com:YOUR_ACCOUNT/YOUR_PROJECT.git
fetch = +refs/heads/:refs/remotes/origin/
Your SSH keys must work locally
Before you can make your keys work through agent forwarding, they must work locally first. Our guide on generating SSH keys can help you set up your SSH keys locally.
Your system must allow SSH agent forwarding
Sometimes, system configurations disallow SSH agent forwarding. You can check if a system configuration file is being used by entering the following command in the terminal:
\$ ssh -v URL
Connect to the specified URL with verbose debug output
OpenSSH_8.1p1, LibreSSL 2.7.3
debug1: Reading configuration data /Users/YOU/.ssh/config
debug1: Applying options for example.com
debug1: Reading configuration data /etc/ssh_config
debug1: Applying options for *
\$ exit
Returns to your local command prompt
In the example above, the file ~/.ssh/config is loaded first, then /etc/ssh_config is read. We can inspect that file to see if it's overriding our options by running the following commands:
\$ cat /etc/ssh_config
Print out the /etc/ssh_config file
Host *
SendEnv LANG LC_*
ForwardAgent no
In this example, our /etc/ssh_config file specifically says ForwardAgent no, which is a way to block agent forwarding. Deleting this line from the file should get agent forwarding working once more.
Your server must allow SSH agent forwarding on inbound connections
Agent forwarding may also be blocked on your server. You can check that agent forwarding is permitted by SSHing into the server and running sshd_config. The output from this command should indicate that AllowAgentForwarding is set.
Your local ssh-agent must be running
On most computers, the operating system automatically launches ssh-agent for you. On Windows, however, you need to do this manually. We have a guide on how to start ssh-agent whenever you open Git Bash.
To verify that ssh-agent is running on your computer, type the following command in the terminal:
\$ echo "$SSH_AUTH_SOCK"
Print out the SSH_AUTH_SOCK variable
/tmp/launch-kNSlgU/Listeners
Your key must be available to ssh-agent
You can check that your key is visible to ssh-agent by running the following command:
ssh-add -L
If the command says that no identity is available, you'll need to add your key:
ssh-add YOUR-KEY
Tip
On macOS, ssh-agent will "forget" this key, once it gets restarted during reboots. But you can import your SSH keys into Keychain using this command:
ssh-add --apple-use-keychain YOUR-KEY
Note
The --apple-use-keychain option stores the passphrase in your keychain for you when you add an SSH key to the ssh-agent. If you chose not to add a passphrase to your key, run the command without the --apple-use-keychain option.
The --apple-use-keychain option is in Apple's standard version of ssh-add. In macOS versions prior to Monterey (12.0), the --apple-use-keychain and --apple-load-keychain flags used the syntax -K and -A, respectively.
If you don't have Apple's standard version of ssh-add installed, you may receive an error. For more information, see Error: ssh-add: illegal option -- apple-use-keychain.
If you continue to be prompted for your passphrase, you may need to add the command to your ~/.zshrc file (or your ~/.bashrc file for bash).>>
<<$ ssh-keygen -p -f ~/.ssh/id_ed25519
Enter old passphrase: [Type old passphrase]
Key has comment 'your_email@example.com'
Enter new passphrase (empty for no passphrase): [Type new passphrase]
Enter same passphrase again: [Repeat the new passphrase]
Your identification has been saved with the new passphrase.>>
<<ssh-add command, and not an application installed by macports, homebrew, or some other external source.
Start the ssh-agent in the background.
\$ eval "$(ssh-agent -s)"
Agent pid 59566
Depending on your environment, you may need to use a different command. For example, you may need to use root access by running sudo -s -H before starting the ssh-agent, or you may need to use exec ssh-agent bash or exec ssh-agent zsh to run the ssh-agent.
If you're using macOS Sierra 10.12.2 or later, you will need to modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain.
First, check to see if your ~/.ssh/config file exists in the default location.
\$ open ~/.ssh/config
The file /Users/YOU/.ssh/config does not exist.
If the file doesn't exist, create the file.
touch ~/.ssh/config
Open your ~/.ssh/config file, then modify the file to contain the following lines. If your SSH key file has a different name or path than the example code, modify the filename or path to match your current setup.
Text
Host GitHub · Build and ship software on a single, collaborative platform 
AddKeysToAgent yes
UseKeychain yes
IdentityFile ~/.ssh/id_ed25519
Note
If you chose not to add a passphrase to your key, you should omit the UseKeychain line.
If you see a Bad configuration option: usekeychain error, add an additional line to the configuration's' Host *.github.com section.
Text
Host GitHub · Build and ship software on a single, collaborative platform 
IgnoreUnknown UseKeychain
Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file.
ssh-add --apple-use-keychain ~/.ssh/id_ed25519
Note
The --apple-use-keychain option stores the passphrase in your keychain for you when you add an SSH key to the ssh-agent. If you chose not to add a passphrase to your key, run the command without the --apple-use-keychain option.
The --apple-use-keychain option is in Apple's standard version of ssh-add. In macOS versions prior to Monterey (12.0), the --apple-use-keychain and --apple-load-keychain flags used the syntax -K and -A, respectively.
If you don't have Apple's standard version of ssh-add installed, you may receive an error. For more information, see Error: ssh-add: illegal option -- apple-use-keychain.
If you continue to be prompted for your passphrase, you may need to add the command to your ~/.zshrc file (or your ~/.bashrc file for bash).
Add the SSH public key to your account on GitHub. For more information, see Adding a new SSH key to your GitHub account.
Generating a new SSH key for a hardware security key
If you are using macOS or Linux, you may need to update your SSH client or install a new SSH client prior to generating a new SSH key. For more information, see Error: Unknown key type.
Insert your hardware security key into your computer.
Open Terminal.
Paste the text below, replacing the email address in the example with the email address associated with your GitHub account.
ssh-keygen -t ed25519-sk -C "your_email@example.com"
Note
If the command fails and you receive the error invalid format or feature not supported, you may be using a hardware security key that does not support the Ed25519 algorithm. Enter the following command instead.
ssh-keygen -t ecdsa-sk -C "your_email@example.com"
When you are prompted, touch the button on your hardware security key.
When you are prompted to "Enter a file in which to save the key," press Enter to accept the default file location.
Enter a file in which to save the key (/Users/YOU/.ssh/id_ed25519_sk): [Press enter]
When you are prompted to type a passphrase, press Enter.
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]>>
<<ssh-keygen -t ed25519 -C "mibnumber001k@gmail.com"
Note
If you are using a legacy system that doesn't support the Ed25519 algorithm, use:
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
This creates a new SSH key, using the provided email as a label.
Generating public/private ALGORITHM key pair.
When you're prompted to "Enter a file in which to save the key", you can press Enter to accept the default file location. Please note that if you created SSH keys previously, ssh-keygen may ask you to rewrite another key, in which case we recommend creating a custom-named SSH key. To do so, type the default file location and replace id_ALGORITHM with your custom key name.
Enter a file in which to save the key (/Users/YOU/.ssh/id_ALGORITHM): [Press enter]
At the prompt, type a secure passphrase. For more information, see Working with SSH key passphrases.
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
Adding your SSH key to the ssh-agent
Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key. When adding your SSH key to the agent, use the default macOS ssh-add command, and not an application installed by macports, homebrew, or some other external source.
Start the ssh-agent in the background.
\$ eval "$(ssh-agent -s)"
Agent pid 59566
<<gpg --default-new-key-algo rsa4096 --gen-key>>
<<gpg --list-secret-keys --keyid-format=long>>
<<$ gpg --list-secret-keys --keyid-format=long
/Users/hubot/.gnupg/secring.gpg
sec 4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid Hubot hubot@example.com
ssb 4096R/4BB6D45482678BE3 2016-03-10
<< gpg --armor --export 3AA5C34371567BD2
Prints the GPG key ID, in ASCII armor format>>
<<<--gpg-sign, unset this configuration so the default format of openpgp will be used.
git config --global --unset gpg.format
Use the gpg --list-secret-keys --keyid-format=long command to list the long form of the GPG keys for which you have both a public and private key. A private key is required for signing commits or tags.
Shell
gpg --list-secret-keys --keyid-format=long
Note
Some GPG installations on Linux may require you to use gpg2 --list-keys --keyid-format LONG to view a list of your existing keys instead. In this case you will also need to configure Git to use gpg2 by running git config --global gpg.program gpg2.
From the list of GPG keys, copy the long form of the GPG key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:
Shell
\$ gpg --list-secret-keys --keyid-format=long
/Users/hubot/.gnupg/secring.gpg
sec 4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid Hubot hubot@example.com
ssb 4096R/4BB6D45482678BE3 2016-03-10
To set your primary GPG signing key in Git, paste the text below, substituting in the GPG primary key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:
git config --global user.signingkey 3AA5C34371567BD2
Alternatively, you may want to use a subkey. In this example, the GPG subkey ID is 4BB6D45482678BE3:
git config --global user.signingkey 4BB6D45482678BE3
If you use multiple keys and subkeys, then you should append an exclamation mark ! to the key to tell git that this is your preferred key. Sometimes you may need to escape the exclamation mark with a back slash: \!.
Optionally, to configure Git to sign all commits and tags by default, enter the following command:
git config --global commit.gpgsign true
git config --global tag.gpgSign true
For more information, see Signing commits.
To add your GPG key to your .bashrc startup file, run the following command:
[ -f ~/.bashrc ] && echo -e '\nexport GPG_TTY=$(tty)' >> ~/.bashrc>>>
<< git config --global gpg.format ssh
To set your SSH signing key in Git, paste the text below, substituting /PATH/TO/.SSH/KEY.PUB with the path to the public key you'd like to use.
git config --global user.signingkey /PATH/TO/.SSH/KEY.PUB>>
<< $ cat ~/.ssh/id_ed25519.pub
Then select and copy the contents of the id_ed25519.pub file
displayed in the terminal to your clipboard>>
<<<>>> from cryptography.hazmat.primitives import hashes
pn = dh.DHParameterNumbers(p, g)
parameters = pn.parameters()
peer_public_numbers = dh.DHPublicNumbers(y, pn)
peer_public_key = peer_public_numbers.public_key()>>>
<<<# Key.file
location:%20/home/linuxbrew%0ANote:%20Homebrew%20is%20pre-installed%20on%20image%20but%20not%20added%20to%20PATH.%0Arun%20the%20eval%20%22$(/home/linuxbrew/.linuxbrew/bin/brew%20shellenv)%22%20command%0Ato%20accomplish%20this.
<<<Location: /home/linuxbrew
Note: Homebrew is pre-installed on image but not added to PATH.
run the eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)" command
to accomplish this.>>
<<Both Xdebug and PCOV extensions are installed, but only Xdebug is enabled.>>
<<User: postgres
PostgreSQL service is disabled by default.
Use the following command as a part of your job to start the service: 'sudo systemctl start postgresql.service'>>
<<User: root
Password: root
MySQL service is disabled by default.
Use the following command as a part of your job to start the service: 'sudo systemctl start mysql.service'>>
<<name: Run commands on different operating systems
on:
push:
branches: [ main ]
pull_request:
branches: [ main ]
jobs:
Run-npm-on-Ubuntu:
name: Run npm on Ubuntu
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@v4
- uses: actions/setup-node@v4
with:
node-version: '14'
- run: npm help
Run-PSScriptAnalyzer-on-Windows:
name: Run PSScriptAnalyzer on Windows
runs-on: windows-latest
steps:
- uses: actions/checkout@v4
- name: Install PSScriptAnalyzer module
shell: pwsh
run: |
Set-PSRepository PSGallery -InstallationPolicy Trusted
Install-Module PSScriptAnalyzer -ErrorAction Stop
- name: Get list of rules
shell: pwsh
run: |
Get-ScriptAnalyzerRule
<<name: Build on Ubuntu
on: push
jobs:
build:
runs-on: ubuntu-latest
steps:
- name: Check out repository code
uses: actions/checkout@v4
- name: Install jq tool
run: |
sudo apt-get update
sudo apt-get install jq
Note
Always run sudo apt-get update before installing a package. In case the apt index is stale, this command fetches and re-indexes any available packages, which helps prevent package installation failures.
Installing software on macOS runners
The following example demonstrates how to install Brew packages and casks as part of a job.
name: Build on macOS
on: push
jobs:
build:
runs-on: macos-latest
steps:
- name: Check out repository code
uses: actions/checkout@v4
- name: Install GitHub CLI
run: |
brew update
brew install gh
- name: Install Microsoft Edge
run: |
brew update
brew install --cask microsoft-edge>>>>>>
<< following git clone command. You would then be prompted to enter your username and password. When prompted for your password, enter your personal access token instead of a password.
\$ git clone https://github.com/USERNAME/REPO.gitConnect your Github account 
Username: YOUR-USERNAME
Password: YOUR-PERSONAL-ACCESS-TOKEN>>
<< "features": {
"ghcr.io/devcontainers/features/github-cli:1": {}
}>>>
<< $ gh at verify -R cli/cli gh_2.62.0_macOS_arm64.zip
Loaded digest sha256:fdb77f31b8a6dd23c3fd858758d692a45f7fc76383e37d475bdcae038df92afc for file://gh_2.62.0_macOS_arm64.zip
Loaded 1 attestation from GitHub API
âœ“ Verification succeeded!
sha256:fdb77f31b8a6dd23c3fd858758d692a45f7fc76383e37d475bdcae038df92afc was attested by:
REPO PREDICATE_TYPE WORKFLOW
cli/cli https://slsa.dev/provenance/v1 .github/workflows/deployment.yml@refs/heads/trunk>>
<< $ cosign verify-blob-attestation --bundle cli-cli-attestation-3120304.sigstore.json \
--new-bundle-format \
--certificate-oidc-issuer="https://token.actions.githubusercontent.com" \
--certificate-identity-regexp="^https://github.com/cli/cli/.github/workflows/deployment.yml@refs/heads/trunk$ " \
gh_2.62.0_macOS_arm64.zip
Verified OK>>
<< $ hub clone rtomayko/tilt
#=> git clone GitHub - rtomayko/tilt: Generic interface to multiple Ruby template engines
or, if you prefer the SSH protocol:
\$ git config --global hub.protocol ssh
\$ hub clone rtomayko/tilt
#=> git clone git@github.com:rtomayko/tilt.git>>
<< steps:
uses: actions/checkout@v2
name: List open pull requests
run: hub pr list
env:
GITHUB_TOKEN: ${{ ##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## }}>>
<< make install:
git clone \
--config transfer.fsckobjects=false \
--config receive.fsckobjects=false \
--config fetch.fsckobjects=false \
GitHub - mislav/hub: A command-line tool that makes git easier to use with GitHub.
cd hub
make install prefix=/usr/local>>
<<docker pull anishathalye/proof-html:1.1.0>>
<<gpg --full-generate-key
If version < 2.1.17, use:
gpg --default-new-key-algo rsa4096 --gen-key>>
<<gpg --list-secret-keys --keyid-format=long>>
<<gpg --armor --export 3AA5C34371567BD2>>
<<git config --global --unset gpg.format>>
<<git config --global user.signingkey 3AA5C34371567BD2
Or using a subkey
git config --global user.signingkey 4BB6D45482678BE3>>
<<cat ~/.ssh/id_ed25519.pub>>
<<git config --global gpg.format ssh
git config --global user.signingkey /PATH/TO/.SSH/KEY.PUB>>
<<[ -f ~/.bashrc ] && echo -e '\nexport GPG_TTY=$(tty)' >> ~/.bashrc>>
<<git config --global user.signingkey 3AA5C34371567BD2
Or using a subkey
git config --global user.signingkey 4BB6D45482678BE3>>
<<gpg --armor --export 3AA5C34371567BD2>>
<<name: Run commands on different operating systems
on:
push:
branches: [ main ]
pull_request:
branches: [ main ]
jobs:
Run-npm-on-Ubuntu:
name: Run npm on Ubuntu
runs-on: ubuntu-latest
steps:
- uses: actions/checkout@v4
- uses: actions/setup-node@v4
with:
node-version: '14'
- run: npm help
Run-PSScriptAnalyzer-on-Windows:
name: Run PSScriptAnalyzer on Windows
runs-on: windows-latest
steps:
- uses: actions/checkout@v4
- name: Install PSScriptAnalyzer module
shell: pwsh
run: |
Set-PSRepository PSGallery -InstallationPolicy Trusted
Install-Module PSScriptAnalyzer -ErrorAction Stop
- name: Get list of rules
shell: pwsh
run: |
Get-ScriptAnalyzerRule>>
<<from cryptography.hazmat.primitives import hashes
from cryptography.hazmat.primitives.asymmetric import dh
from cryptography.hazmat.primitives.kdf.hkdf import HKDF
Generate parameters
parameters = dh.generate_parameters(generator=2, key_size=2048)
Generate private keys
server_private_key = parameters.generate_private_key()
peer_private_key = parameters.generate_private_key()
Exchange keys and derive shared key
shared_key = server_private_key.exchange(peer_private_key.public_key())
derived_key = HKDF(
algorithm=hashes.SHA256(),
length=32,
salt=None,
info=b'handshake data',
).derive(shared_key)
Verify same derived key
same_shared_key = peer_private_key.exchange(server_private_key.public_key())
same_derived_key = HKDF(
algorithm=hashes.SHA256(),
length=32,
salt=None,
info=b'handshake data',
).derive(same_shared_key)
assert derived_key == same_derived_key>>
AuthenticatedCARD.md | 2195 ++++++++++++++++++++++++++++++++++++++++++
1 file changed, 2195 insertions(+)
create mode 100644 AuthenticatedCARD.md
diff --git a/AuthenticatedCARD.md b/AuthenticatedCARD.md
new file mode 100644
index 0000000..ab43eef
--- /dev/null
+++ b/AuthenticatedCARD.md
@@ -0,0 +1,2195 @@
+<<<<PATH>>>>
+
+<<Cancel.
+
GET_CONFIRMATION description>>
 
+<<use this for token inputs: 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>>
+
+
+<<PRESET_PASSPHRASE [--inquire] <string_or_keygrip> <timeout> [<hexstring>]>>
+
+<<HAVEKEY keygrips>>
+
+<<smartcard
+
LEARN [--send]
+This command is used to register a smartcard. With the --send option given the certificates are sent back.>>
 
+<<GETEVENTCOUNTER
+This>>
+
+<< gpg-connect-agent --dirmngr 'loadswdb --force' /bye
+--keyserver name
+Use name as your keyserver. This is the server that gpg communicates with to receive keys, send keys, and search for keys. The format of the name is a URI: â€˜scheme:[//]keyservername[:port]â€™ The scheme is the type of keyserver: "hkp" for the HTTP (or compatible) keyservers or "ldap" for the LDAP keyservers. Note that your particular installation of GnuPG may have other keyserver types available as well. Keyserver schemes are case-insensitive. After the keyserver name, optional keyserver configuration options may be provided. These are the same as the --keyserver-options of gpg, but apply only to this particular keyserver.
+
+Some keyservers synchronize with each other, so there is not always a need to send keys to more than one server. Some keyservers use round robin DNS to give a different keyserver each time you use it.
+
+If exactly two keyservers are configured and only one is a Tor hidden service (.onion), Dirmngr selects the keyserver to use depending on whether Tor is locally running or not. The check for a running Tor is done for each new connection.
+
+If no keyserver is explicitly configured, dirmngr will use the built-in default of https://keyserver.ubuntu.com. To avoid the use of a default keyserver the value none can be used.
+
+Windows users with a keyserver running on their Active Directory may use the short form ldap:/// for name to access this directory.
+
+For accessing anonymous LDAP keyservers name is in general just a ldaps://ldap.example.com. A BaseDN parameter should never be specified. If authentication is required things are more complicated and two methods are available:
+
+The modern method (since version 2.2.28) is to use the very same syntax as used with the option --ldapserver. Please see over there for details; here is an example:
+
keyserver ldap:ldap.example.com::uid=USERNAME,ou=GnuPG Users,
dc=example,dc=com:PASSWORD::starttls
+The other method is to use a full URL for name; for example:
+
keyserver ldaps://ldap.example.com/????bindname=uid=USERNAME
%2Cou=GnuPG%20Users%2Cdc=example%2Cdc=com,password=PASSWORD
+Put>>
+
+
+<<<System
+These System root certificates are used by: FIXME
+
+The origin of the system provided certificates depends on the platform. On Windows all certificates from the Windows System Stores ROOT and CA are used.
+
+On other platforms the certificates are read from the first file found form this list: /etc/ssl/ca-bundle.pem, /etc/ssl/certs/ca-certificates.crt, /etc/pki/tls/cert.pem, /usr/local/share/certs/ca-root-nss.crt, /etc/ssl/cert.pem.
+
+GnuPG
+The GnuPG specific certificates stored in the directory /etc/gnupg/trusted-certs are only used to validate CRLs.
+
+OpenPGP keyserver
+For accessing the OpenPGP keyservers the only certificates used are those set with the configuration option hkp-cacert.
+
+OpenPGP keyserver pool
+This is usually only one certificate read from the file /usr/local/share/gnupg/gnupg/sks-keyservers.netCA.pem. If this certificate exists it is used to access the special keyservers hkps.pool.sks-keyservers.net (or hkps://keys.gnupg.net).
+
+Please note that gpgsm accepts Root CA certificates for its own purposes only if they are listed in its file trustlist.txt. dirmngr does not make use of this list - except FIXME.
+
+To be able to see diagnostics it is often useful to put at least the following lines into the configuration file ~/gnupg/dirmngr.conf:
+
+log-file ~/dirmngr.log
+verbose
+You may want to check the log file to see whether all desired root CA certificates are correctly loaded.
+
+To be able to perform OCSP requests you probably want to add the line:
+
+allow-ocsp
+To make sure that new options are read or that after the installation of a new GnuPG versions the right dirmngr version is running, you should kill an existing dirmngr so that a new instance is started as needed by the other components:
+
+gpgconf --kill dirmngr
+Direct interfaction with the dirmngr is possible by using the command
+
+gpg-connect-agent --dirmngr>>>
+
+<<SIGHUP
+This signal flushes all internally cached CRLs as well as any cached certificates. Then the certificate cache is reinitialized as on startup. Options are re-read from the configuration file. Instead of sending this signal it is better to use
+
+gpgconf --reload dirmngr
+SIGTERM
+Shuts down the process but waits until all current requests are fulfilled. If the process has received 3 of these signals and requests are still pending, a shutdown is forced. You may also use
+
+gpgconf --kill dirmngr
+instead of this signal
+
+SIGINT
+Shuts down the process immediately.
+
+SIGUSR1>>
+
+<<API.
+
gpg-connect-agent --dirmngr 'keyserver --hosttable' /bye
+To inhibit the use of a particular host you have noticed in one of the keyserver pools, you may use
 
gpg-connect-agent --dirmngr 'keyserver --dead pgpkeys.bnd.de' /bye
+The description of the keyserver command can be printed using
 
gpg-connect-agent --dirmngr 'help keyserver' /bye>>
 
+<<3.6.1 Return the certificate(s) found
+
+Lookup certificate. To allow multiple patterns (which are ORed) quoting is required: Spaces are to be translated into "+" or into "%20"; obviously this requires that the usual escape quoting rules are applied. The server responds with:
+
S: D <DER encoded certificate>
S: END
S: D <second DER encoded certificate>
S: END
S: OK
+In this example 2 certificates are returned. The server may return any number of certificates; OK will also be returned when no certificates were found. The dirmngr might return a status line
 
S: S TRUNCATED <n>
+To indicate that the output was truncated to N items due to a limitation of the server or by an arbitrary set limit.
 
+The option --url may be used if instead of a search pattern a complete URL to the certificate is known:
+
C: LOOKUP --url CN%3DWerner%20Koch,o%3DIntevation%20GmbH,c%3DDE?userCertificate
+If the option --cache-only is given, no external lookup is done so that only certificates from the cache are returned.
 
+With the option --single, the first and only the first match will be returned. Unless option --cache-only is also used, no local lookup will be done in this case.>>>
+
+<<ISVALID [--only-ocsp] [--force-default-responder] certid|certfpr>>
+
+<< S: INQUIRE SENDCERT <CertID>
C: D <DER encoded certificate>
C: END
+A client should be aware that DirMngr may ask for more than one certificate.
 
+If Dirmngr has a certificate but the signature of the certificate could not been validated because the root certificate is not known to dirmngr as trusted, it may ask back to see whether the client trusts this the root certificate:
+
S: INQUIRE ISTRUSTED <CertHexfpr>
C: D 1
C: END>>
 
+<<
+Check whether the certificate with FINGERPRINT (SHA-1 hash of the entire X.509 certificate blob) is valid or not by consulting the CRL responsible for this certificate. If the fingerprint has not been given or the certificate is not known, the function inquires the certificate using:
+
S: INQUIRE TARGETCERT
C: D <DER encoded certificate>
C: END
+Thus the caller is expected to return the certificate for the request (which should match FINGERPRINT) as a binary blob. Processing then takes place without further interaction; in particular dirmngr tries to locate other required certificate by its own mechanism which includes a local certificate store as well as a list of trusted root certificates.
 
+The return code is 0 for success; i.e. the certificate has not been revoked or one of the usual error codes from libgpg-error.>>
+
+<<OCSP
+
CHECKOCSP [--force-default-responder] [fingerprint]
+Check whether the certificate with fingerprint (the SHA-1 hash of the entire X.509 certificate blob) is valid by consulting the appropriate OCSP responder. If the fingerprint has not been given or the certificate is not known by Dirmngr, the function inquires the certificate using:
 
S: INQUIRE TARGETCERT
C: D <DER encoded certificate>
C: END
+Thus the caller is expected to return the certificate for the request (which should match fingerprint) as a binary blob. Processing then takes place without further interaction; in particular dirmngr tries to locate other required certificates by its own mechanism which includes a local certificate store as well as a list of trusted root certificates.
 
+If the option --force-default-responder is given, only the default OCSP responder is used. This option is the per-command variant of the global option --ignore-ocsp-service-url.>>
+
+<<using>>
+
<<S: INQUIRE TARGETCERT
C: D <DER encoded certificate>
C: END>>
 
 
 
 
+<<using
+
S: INQUIRE TARGETCERT
C: D <DER encoded certificate>
C: END>>
 
 
+<<command>> <--edit-key>>
+
+
+<<$ export GNUPGHOME="$(mktemp -d)"
+$ cat >foo <<EOF
%echo Generating a basic OpenPGP key
Key-Type: DSA
Key-Length: 1024
Subkey-Type: ELG-E
Subkey-Length: 1024
Name-Real: Joe Tester
Name-Comment: with stupid passphrase
Name-Email: joe@foo.bar
Expire-Date: 0
Passphrase: abc
# Do a commit here, so that we can later print "done" :-)
%commit
%echo done
+EOF
+$ gpg --batch --generate-key foo
[...]
+$ gpg --list-secret-keys
+/tmp/tmp.0NQxB74PEf/pubring.kbx
+-------------------------------
+sec dsa1024 2016-12-16 [SCA]
768E895903FC1C44045C8CB95EEBDB71E9E849D0
+uid [ultimate] Joe Tester (with stupid passphrase) joe@foo.bar
+ssb elg1024 2016-12-16 [E]
+If you want to create a key with the default algorithms you would use these parameters:
+
%echo Generating a default key
Key-Type: default
Subkey-Type: default
Name-Real: Joe Tester
Name-Comment: with stupid passphrase
Name-Email: joe@foo.bar
Expire-Date: 0
Passphrase: abc
# Do a commit here, so that we can later print "done" :-)
%commit
%echo done>>
 
+<<GENKEY
+GPGSM checks whether this command is allowed and then does an INQUIRY to get the key parameters, the client should then send the key parameters in the native format:
+
S: INQUIRE KEY_PARAM native
C: D foo:fgfgfg
C: D bar
C: END>>
 
+<<command:
+
LISTKEYS pattern
+is used. To allow multiple patterns (which are ORed during the search) quoting is required: Spaces are to be translated into "+" or into "%20"; in turn this requires that the usual escape quoting rules are done.
 
LISTSECRETKEYS pattern
+Lists only the keys where a secret key is available.
 
+The list commands are affected by the option
+
OPTION list-mode=mode>>
 
+<<EXPORT [--data [--armor] [--base64]] [--] pattern>>
+
+<<IMPORT [--re-import]>>
+
+<<YUBIKEY cmd args
+Various commands pertaining to Yubikey tokens with cmd being:
+
+LIST
+List supported and enabled Yubikey applications.
+
+ENABLE usb|nfc|all [otp|u2f|opgp|piv|oath|fido2|all]
+DISABLE
+Enable or disable the specified or all applications on the given interface.
+
+The support for OpenPGP cards in gpg-card is not yet complete. For missing features, please continue to use gpg --card-edit.
+
+GnuPG has support for PIV cards (â€œPersonal Identity Verificationâ€ as specified by NIST Special Publication 800-73-4). This section describes how to initialize (personalize) a fresh Yubikey token featuring the PIV application (requires Yubikey-5). We assume that the credentials have not yet been changed and thus are:
+
+Authentication key
+This is a 24 byte key described by the hex string
+010203040506070801020304050607080102030405060708.
+
+PIV Application PIN
+This is the string 123456.
+
+PIN Unblocking Key
+This is the string 12345678.
+
+See the example section on how to change these defaults. For production use it is important to use secure values for them. Note that the Authentication Key is not queried via the usual Pinentry dialog but needs to be entered manually or read from a file. The use of a dedicated machine to personalize tokens is strongly suggested.
+
+To see what is on the card, the command list can be given. We will use the interactive mode in the following (the string gpg/card> is the prompt). An example output for a fresh card is:
+
+gpg/card> list
+Reader ...........: 1050:0407:X:0
+Card type ........: yubikey
+Card firmware ....: 5.1.2
+Serial number ....: D2760001240102010006090746250000
+Application type .: OpenPGP
+Version ..........: 2.1
+[...]
+It can be seen by the â€œApplication typeâ€ line that GnuPG selected the OpenPGP application of the Yubikey. This is because GnuPG assigns the highest priority to the OpenPGP application. To use the PIV application of the Yubikey several methods can be used:
+
+With a Yubikey 5 or later the OpenPGP application on the Yubikey can be disabled:
+
+gpg/card> yubikey disable all opgp
+gpg/card> yubikey list
+Application USB NFC
+-----------------------
+OTP yes yes
+U2F yes yes
+OPGP no no
+PIV yes no
+OATH yes yes
+FIDO2 yes yes
+gpg/card> reset
+The reset is required so that the GnuPG system rereads the card. Note that disabled applications keep all their data and can at any time be re-enabled (use help yubikey).
+
+Another option, which works for all Yubikey versions, is to disable the support for OpenPGP cards in scdaemon. This is done by adding the line
+
+disable-application openpgp
+to ~/.gnupg/scdaemon.conf and by restarting scdaemon, either by killing the process or by using gpgconf --kill scdaemon. Finally the default order in which card applications are tried by scdaemon can be changed. For example to prefer PIV over OpenPGP it is sufficient to add
+
+application-priority piv
+to ~/.gnupg/scdaemon.conf and to restart scdaemon. This has an effect only on tokens which support both, PIV and OpenPGP, but does not hamper the use of OpenPGP only tokens.
+
+With one of these methods employed the list command of gpg-card shows this:
+
+gpg/card> list
+Reader ...........: 1050:0407:X:0
+Card type ........: yubikey
+Card firmware ....: 5.1.2
+Serial number ....: FF020001008A77C1
+Application type .: PIV
+Version ..........: 1.0
+Displayed s/n ....: yk-9074625
+PIN usage policy .: app-pin
+PIN retry counter : - 3 -
+PIV authentication: [none]
keyref .....: PIV.9A
+Card authenticat. : [none]
keyref .....: PIV.9E
+Digital signature : [none]
keyref .....: PIV.9C
+Key management ...: [none]
keyref .....: PIV.9D
+In case several tokens are plugged into the computer, gpg-card will show only one. To show another token the number of the token (0, 1, 2, ...) can be given as an argument to the list command. The command list --cards prints a list of all inserted tokens.
+
+Note that the â€œDisplayed s/nâ€ is printed on the token and also shown in Pinentry prompts asking for the PIN. The four standard key slots are always shown, if other key slots are initialized they are shown as well. The PIV authentication key (internal reference PIV.9A) is used to authenticate the card and the card holder. The use of the associated private key is protected by the Application PIN which needs to be provided once and the key can the be used until the card is reset or removed from the reader or USB port. GnuPG uses this key with its Secure Shell support. The Card authentication key (PIV.9E) is also known as the CAK and used to support physical access applications. The private key is not protected by a PIN and can thus immediately be used. The Digital signature key (PIV.9C) is used to digitally sign documents. The use of the associated private key is protected by the Application PIN which needs to be provided for each signing operation. The Key management key (PIV.9D) is used for encryption. The use of the associated private key is protected by the Application PIN which needs to be provided only once so that decryption operations can then be done until the card is reset or removed from the reader or USB port.
+
+We now generate three of the four keys. Note that GnuPG does currently not use the the Card authentication key; however, that key is mandatory by the PIV standard and thus we create it too. Key generation requires that we authenticate to the card. This can be done either on the command line (which would reveal the key):
+
+gpg/card> auth 010203040506070801020304050607080102030405060708
+or by reading the key from a file. That file needs to consist of one LF terminated line with the hex encoded key (as above):
+
+gpg/card> auth < myauth.key
+As usual â€˜help authâ€™ gives help for this command. An error message is printed if a non-matching key is used. The authentication is valid until a reset of the card or until the card is removed from the reader or the USB port. Note that that in non-interactive mode the â€˜<â€™ needs to be quoted so that the shell does not interpret it as a its own redirection symbol.
+
+Here are the actual commands to generate the keys:
+
+gpg/card> generate --algo=nistp384 PIV.9A
+PIV card no. yk-9074625 detected
+gpg/card> generate --algo=nistp256 PIV.9E
+PIV card no. yk-9074625 detected
+gpg/card> generate --algo=rsa2048 PIV.9C
+PIV card no. yk-9074625 detected
+If a key has already been created for one of the slots an error will be printed; to create a new key anyway the option â€˜--forceâ€™ can be used. Note that only the private and public keys have been created but no certificates are stored in the key slots. In fact, GnuPG uses its own non-standard method to store just the public key in place of the the certificate. Other application will not be able to make use these keys until gpgsm or another tool has been used to create and store the respective certificates. Let us see what the list command now shows:
+
+gpg/card> list
+Reader ...........: 1050:0407:X:0
+Card type ........: yubikey
+Card firmware ....: 5.1.2
+Serial number ....: FF020001008A77C1
+Application type .: PIV
+Version ..........: 1.0
+Displayed s/n ....: yk-9074625
+PIN usage policy .: app-pin
+PIN retry counter : - 3 -
+PIV authentication: 213D1825FDE0F8240CB4E4229F01AF90AC658C2E
keyref .....: PIV.9A (auth)
algorithm ..: nistp384
+Card authenticat. : 7A53E6CFFE7220A0E646B4632EE29E5A7104499C
keyref .....: PIV.9E (auth)
algorithm ..: nistp256
+Digital signature : 32A6C6FAFCB8421878608AAB452D5470DD3223ED
keyref .....: PIV.9C (sign,cert)
algorithm ..: rsa2048
+Key management ...: [none]
keyref .....: PIV.9D
+The primary information for each key is the keygrip, a 40 byte hex-string identifying the key. This keygrip is a unique identifier for the specific parameters of a key. It is used by gpg-agent and other parts of GnuPG to associate a private key to its protocol specific certificate format (X.509, OpenPGP, or SecureShell). Below the keygrip the key reference along with the key usage capabilities are show. Finally the algorithm is printed in the format used by gpg. At that point no other information is shown because for these new keys gpg wonâ€™t be able to find matching certificates.
+
+Although we could have created the Key management key also with the generate command, we will create that key off-card so that a backup exists. To accomplish this a key needs to be created with either gpg or gpgsm or imported in one of these tools. In our example we create a self-signed X.509 certificate (exit the gpg-card tool, first):
+
+$ gpgsm --gen-key -o encr.crt
(1) RSA
(2) Existing key
(3) Existing key from card
+Your selection? 1
+What keysize do you want? (3072) 2048
+Requested keysize is 2048 bits
+Possible actions for a RSA key:
(1) sign, encrypt
(2) sign
(3) encrypt
+Your selection? 3
+Enter the X.509 subject name: CN=Encryption key for yk-9074625,O=example,C=DE
+Enter email addresses (end with an empty line):
+> otto@example.net
+>
+Enter DNS names (optional; end with an empty line):
+>
+Enter URIs (optional; end with an empty line):
+>
+Create self-signed certificate? (y/N) y
+These parameters are used:
Key-Type: RSA
Key-Length: 2048
Key-Usage: encrypt
Serial: random
Name-DN: CN=Encryption key for yk-9074625,O=example,C=DE
Name-Email: otto@example.net
 
+Proceed with creation? (y/N)
+Now creating self-signed certificate. This may take a while ...
+gpgsm: about to sign the certificate for key: &34798AAFE0A7565088101CC4AE31C5C8C74461CB
+gpgsm: certificate created
+Ready.
+$ gpgsm --import encr.crt
+gpgsm: certificate imported
+gpgsm: total number processed: 1
+gpgsm: imported: 1
+Note the last step which imported the created certificate. If you you instead created a certificate signing request (CSR) instead of a self-signed certificate and sent this off to a CA you would do the same import step with the certificate received from the CA. Take note of the keygrip (prefixed with an ampersand) as shown during the certificate creation or listed it again using â€˜gpgsm --with-keygrip -k otto@example.netâ€™. Now to move the key and certificate to the card start gpg-card again and enter:
+
+gpg/card> writekey PIV.9D 34798AAFE0A7565088101CC4AE31C5C8C74461CB
+gpg/card> writecert PIV.9D < encr.crt
+If you entered a passphrase to protect the private key, you will be asked for it via the Pinentry prompt. On success the key and the certificate has been written to the card and a list command shows:
+
+[...]
+Key management ...: 34798AAFE0A7565088101CC4AE31C5C8C74461CB
keyref .....: PIV.9D (encr)
algorithm ..: rsa2048
used for ...: X.509
user id ..: CN=Encryption key for yk-9074625,O=example,C=DE
user id ..: <otto@example.net>
+In case the same key (identified by the keygrip) has been used for several certificates you will see several â€œused forâ€ parts. With this the encryption key is now fully functional and can be used to decrypt messages encrypted to this certificate. TAKE CARE: the original key is still stored on-disk and should be moved to a backup medium. This can simply be done by copying the file 34798AAFE0A7565088101CC4AE31C5C8C74461CB.key from the directory ~/.gnupg/private-keys-v1.d/ to the backup medium and deleting the file at its original place.
+
+The final example is to create a self-signed certificate for digital signatures. Leave gpg-card using quit or by pressing Control-D and use gpgsm:
+
+$ gpgsm --learn
+$ gpgsm --gen-key -o sign.crt
+Please select what kind of key you want:
(1) RSA
(2) Existing key
(3) Existing key from card
+Your selection? 3
+Serial number of the card: FF020001008A77C1
+Available keys:
(1) 213D1825FDE0F8240CB4E4229F01AF90AC658C2E PIV.9A nistp384
(2) 7A53E6CFFE7220A0E646B4632EE29E5A7104499C PIV.9E nistp256
(3) 32A6C6FAFCB8421878608AAB452D5470DD3223ED PIV.9C rsa2048
(4) 34798AAFE0A7565088101CC4AE31C5C8C74461CB PIV.9D rsa2048
+Your selection? 3
+Possible actions for a RSA key:
(1) sign, encrypt
(2) sign
(3) encrypt
+Your selection? 2
+Enter the X.509 subject name: CN=Signing key for yk-9074625,O=example,C=DE
+Enter email addresses (end with an empty line):
+> otto@example.net
+>
+Enter DNS names (optional; end with an empty line):
+>
+Enter URIs (optional; end with an empty line):
+>
+Create self-signed certificate? (y/N)
+These parameters are used:
Key-Type: card:PIV.9C
Key-Length: 1024
Key-Usage: sign
Serial: random
Name-DN: CN=Signing key for yk-9074625,O=example,C=DE
Name-Email: otto@example.net
 
+Proceed with creation? (y/N) y
+Now creating self-signed certificate. This may take a while ...
+gpgsm: about to sign the certificate for key: &32A6C6FAFCB8421878608AAB452D5470DD3223ED
+gpgsm: certificate created
+Ready.
+$ gpgsm --import sign.crt
+gpgsm: certificate imported
+gpgsm: total number processed: 1
+gpgsm: imported: 1
+The use of â€˜gpgsm --learnâ€™ is currently necessary so that gpg-agent knows what keys are available on the card. The need for this command will eventually be removed. The remaining commands are similar to the creation of an on-disk key. However, here we select the â€˜Digital signatureâ€™ key. During the creation process you will be asked for the Application PIN of the card. The final step is to write the certificate to the card using gpg-card:
+
+gpg/card> writecert PIV.9C < sign.crt
+By running list again we will see the fully initialized card:
+
+Reader ...........: 1050:0407:X:0
+Card type ........: yubikey
+Card firmware ....: 5.1.2
+Serial number ....: FF020001008A77C1
+Application type .: PIV
+Version ..........: 1.0
+Displayed s/n ....: yk-9074625
+PIN usage policy .: app-pin
+PIN retry counter : - [verified] -
+PIV authentication: 213D1825FDE0F8240CB4E4229F01AF90AC658C2E
keyref .....: PIV.9A (auth)
algorithm ..: nistp384
+Card authenticat. : 7A53E6CFFE7220A0E646B4632EE29E5A7104499C
keyref .....: PIV.9E (auth)
algorithm ..: nistp256
+Digital signature : 32A6C6FAFCB8421878608AAB452D5470DD3223ED
keyref .....: PIV.9C (sign,cert)
algorithm ..: rsa2048
used for ...: X.509
user id ..: CN=Signing key for yk-9074625,O=example,C=DE
user id ..: <otto@example.net>
+Key management ...: 34798AAFE0A7565088101CC4AE31C5C8C74461CB
keyref .....: PIV.9D (encr)
algorithm ..: rsa2048
used for ...: X.509
user id ..: CN=Encryption key for yk-9074625,O=example,C=DE
user id ..: <otto@example.net>
+It is now possible to sign and to encrypt with this card using gpgsm and to use the â€˜PIV authenticationâ€™ key with ssh:
+
+$ ssh-add -l
+384 SHA256:0qnJ0Y0ehWxKcx2frLfEljf6GCdlO55OZed5HqGHsaU cardno:yk-9074625 (ECDSA)
+As usual use ssh-add with the uppercase â€˜-Lâ€™ to list the public ssh key. To use the certificates with Thunderbird or Mozilla, please consult the Scute manual for details.
+
+If you want to use the same PIV keys also for OpenPGP (for example on a Yubikey to avoid switching between OpenPGP and PIV), this is also possible:
+
+$ gpgsm --learn
+$ gpg --full-gen-key
+Please select what kind of key you want:
(1) RSA and RSA (default)
(2) DSA and Elgamal
(3) DSA (sign only)
(4) RSA (sign only)
(14) Existing key from card
+Your selection? 14
+Serial number of the card: FF020001008A77C1
+Available keys:
(1) 213D1825FDE0F8240CB4E4229F01AF90AC658C2E PIV.9A nistp384 (auth)
(2) 7A53E6CFFE7220A0E646B4632EE29E5A7104499C PIV.9E nistp256 (auth)
(3) 32A6C6FAFCB8421878608AAB452D5470DD3223ED PIV.9C rsa2048 (cert,sign)
(4) 34798AAFE0A7565088101CC4AE31C5C8C74461CB PIV.9D rsa2048 (encr)
+Your selection? 3
+Please specify how long the key should be valid.
0 = key does not expire
<n> = key expires in n days
<n>w = key expires in n weeks
<n>m = key expires in n months
<n>y = key expires in n years
+Key is valid for? (0)
+Key does not expire at all
+Is this correct? (y/N) y
+
+GnuPG needs to construct a user ID to identify your key.
+
+Real name:
+Email address: otto@example.net
+Comment:
+You selected this USER-ID:
"otto@example.net"
 
+Change (N)ame, (C)omment, (E)mail or (O)kay/(Q)uit? o
+gpg: key C3AFA9ED971BB365 marked as ultimately trusted
+gpg: revocation certificate stored as '[...]D971BB365.rev'
+public and secret key created and signed.
+
+Note that this key cannot be used for encryption. You may want to use
+the command "--edit-key" to generate a subkey for this purpose.
+pub rsa2048 2019-04-04 [SC]
7F899AE2FB73159DD68A1B20C3AFA9ED971BB365
+uid otto@example.net
+Note that you will be asked two times to enter the PIN of your PIV card. If you run gpg in --expert mode you will also ge given the option to change the usage flags of the key. The next typescript shows how to add the encryption subkey:
+
+$ gpg --edit-key 7F899AE2FB73159DD68A1B20C3AFA9ED971BB365
+Secret key is available.
+
+sec rsa2048/C3AFA9ED971BB365
created: 2019-04-04 expires: never usage: SC
card-no: FF020001008A77C1
trust: ultimate validity: ultimate
+[ultimate] (1). otto@example.net
+gpg> addkey
+Secret parts of primary key are stored on-card.
+Please select what kind of key you want:
(3) DSA (sign only)
(4) RSA (sign only)
(5) Elgamal (encrypt only)
(6) RSA (encrypt only)
(14) Existing key from card
+Your selection? 14
+Serial number of the card: FF020001008A77C1
+Available keys:
(1) 213D1825FDE0F8240CB4E4229F01AF90AC658C2E PIV.9A nistp384 (auth)
(2) 7A53E6CFFE7220A0E646B4632EE29E5A7104499C PIV.9E nistp256 (auth)
(3) 32A6C6FAFCB8421878608AAB452D5470DD3223ED PIV.9C rsa2048 (cert,sign)
(4) 34798AAFE0A7565088101CC4AE31C5C8C74461CB PIV.9D rsa2048 (encr)
+Your selection? 4
+Please specify how long the key should be valid.
0 = key does not expire
<n> = key expires in n days
<n>w = key expires in n weeks
<n>m = key expires in n months
<n>y = key expires in n years
+Key is valid for? (0)
+Key does not expire at all
+Is this correct? (y/N) y
+Really create? (y/N) y
+
+sec rsa2048/C3AFA9ED971BB365
created: 2019-04-04 expires: never usage: SC
card-no: FF020001008A77C1
trust: ultimate validity: ultimate
+ssb rsa2048/7067860A98FCE6E1
created: 2019-04-04 expires: never usage: E
card-no: FF020001008A77C1
+[ultimate] (1). otto@example.net
+
+gpg> save>>
+<<query {
viewer {
login
}
+}>>
+<<array.
 
+{
"data": null,
"errors": [
{
"message": "Objects must have selections (field 'nodes' returns Repository but has no selections)",
"locations": [
{
"line": 5,
"column": 8
}
]
}
]
+}
+It's possible you might run into an unexpected error that is not related to the schema. If this happens, the message will include a reference code you can use when reporting the issue:
 
+{
"data": null,
"errors": [
{
"message": "Something went wrong while executing your query. This is most likely a GitHub bug. Please include \\"7571:3FF6:552G94B:69F45B7:5913BBEQ\\" when reporting this issue."
}
]
+}>>
 
+<<Here's a contrived example of a schema that defines interface X and object Y:
+
+interface X {
some_field: String!
other_field: String!
+}
 
+type Y implements X {
some_field: String!
other_field: String!
new_field: String!
+}>>
+<<Query __schema to list all types defined in the schema and get details about each:
 
+query {
__schema {
types {
name
kind
description
fields {
name
}
}
}
+}
+Query __type to get details about any type:
 
+query {
__type(name: "Repository") {
name
kind
description
fields {
name
}
}
+}
+You can also run an introspection query of the schema via a GET request:
 
+curl -H "Authorization: bearer TOKEN" https://api.github.com/graphql
+Note
+
+If you get the response "message": "Bad credentials" or 401 Unauthorized, check that you are using a valid token. If you receive a 403 error with Resource not accessible by personal access token, ensure that your fine-grained personal access token is targeted to the correct resource owner. For example, it must target the organization that owns the repository you are trying to access.
+The results are in JSON, so we recommend pretty-printing them for easier reading and searching. You can use a command-line tool like jq or pipe the results into python -m json.tool for this purpose.
+
+Alternatively, you can pass the idl media type to return the results in IDL format, which is a condensed version of the schema:
+
+$ curl -H "Authorization: bearer TOKEN" -H "Accept: application/vnd.github.v4.idl" \
+https://api.github.com/graphql>>
+<<curl -i --header "Authorization: Bearer YOUR-TOKEN" https://api.github.com/user
+you'll get a response that includes the node_id of the authenticated user:
+
+{
"login": "octocat",
"id": 1,
"avatar_url": "https://github.com/images/error/octocat_happy.gif",
"gravatar_id": "",
"url": "https://api.github.com/users/octocat",
"html_url": "octocat - Overview ",
"followers_url": "https://api.github.com/users/octocat/followers",
"following_url": "https://api.github.com/users/octocat/following{/other_user}",
"gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
"starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
"subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
"organizations_url": "https://api.github.com/users/octocat/orgs",
"repos_url": "https://api.github.com/users/octocat/repos",
"events_url": "https://api.github.com/users/octocat/events{/privacy}",
"received_events_url": "https://api.github.com/users/octocat/received_events",
"type": "User",
"site_admin": false,
"name": "monalisa octocat",
"company": "GitHub",
"blog": "https://github.com/blog",
"location": "San Francisco",
"email": "octocat@github.com",
"hireable": false,
"bio": "There once was...",
"public_repos": 2,
"public_gists": 1,
"followers": 20,
"following": 0,
"created_at": "2008-01-14T04:33:35Z",
"updated_at": "2008-01-14T04:33:35Z",
"private_gists": 81,
"total_private_repos": 100,
"owned_private_repos": 100,
"disk_usage": 10000,
"collaborators": 8,
"two_factor_authentication": true,
"plan": {
"name": "Medium",
"space": 400,
"private_repos": 20,
"collaborators": 0
},
"node_id": "MDQ6VXNlcjU4MzIzMQ=="
+}
+2. Find the object type in GraphQL
 
+In this example, the node_id value is MDQ6VXNlcjU4MzIzMQ==. You can use this value to query the same object in GraphQL.
+
+You'll need to know the object's type first, though. You can check the type with a simple GraphQL query:
+
+query {
node(id:"MDQ6VXNlcjU4MzIzMQ==") {
__typename
}
+}
+This type of queryâ€”that is, finding the node by IDâ€”is known as a "direct node lookup."
 
+When you run this query, you'll see that the __typename is User.
+
+3. Do a direct node lookup in GraphQL
+
+Once you've confirmed the type, you can use an inline fragment to access the object by its ID and return additional data. In this example, we define the fields on User that we'd like to query:
+
+query {
node(id:"MDQ6VXNlcjU4MzIzMQ==") {
... on User {
name
login
}
}
+}>>>
+<token:##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##>
+<<curl -L \
-H "Accept: application/vnd.github+json" \
-H "Authorization: Bearer <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>" \
-H "X-GitHub-Api-Version: 2022-11-28" \
https://api.github.com/user
+<<curl -L \
-X PATCH \
-H "Accept: application/vnd.github+json" \
-H "Authorization: Bearer <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>" \
-H "X-GitHub-Api-Version: 2022-11-28" \
https://api.github.com/user \
-d '{"blog":"https://github.com/blog","name":"monalisa octocat"}'>>
 
+<<http://api.github.com >> with your enterprise's dedicated subdomain at <<api.SUBDOMAIN.ghe.com>>
+
+<<name: Context testing
+on: push
+
+jobs:
dump_contexts_to_log:
runs-on: ubuntu-latest
steps:
```
name: Dump GitHub context ```
env:
GITHUB_CONTEXT: ${{ toJson(github) }}
run: echo "$GITHUB_CONTEXT"
```
name: Dump job context ```
env:
JOB_CONTEXT: ${{ toJson(job) }}
run: echo "$JOB_CONTEXT"
```
name: Dump steps context ```
env:
STEPS_CONTEXT: ${{ toJson(steps) }}
run: echo "$STEPS_CONTEXT"
```
name: Dump runner context ```
env:
RUNNER_CONTEXT: ${{ toJson(runner) }}
run: echo "$RUNNER_CONTEXT"
```
name: Dump strategy context ```
env:
STRATEGY_CONTEXT: ${{ toJson(strategy) }}
run: echo "$STRATEGY_CONTEXT"
```
name: Dump matrix context ```
env:
MATRIX_CONTEXT: ${{ toJson(matrix) }}
run: echo "$MATRIX_CONTEXT"
+>>
+jobs:
use_api:
runs-on: ubuntu-latest
permissions: {}
steps:
```
env: ```
GH_TOKEN: ${{ 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 }}
run: |
curl --request GET \\
--url "<https://api.github.com/PATH>" \\
--header "Authorization: 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"
 
 
+<curl> <<GITHUB_TOKEN>> as an environment variable, and use the <run> keyword to execute the GitHub CLI <api> subcommand. For more information about the run keyword, see Workflow syntax for GitHub Actions.
+
+In the following example workflow, replace PATH with the path of the endpoint. For more information about the path, see Getting started with the REST API.
+
+<<jobs:
use_api:
runs-on: ubuntu-latest
permissions: {}
steps:
```
env: ```
GH_TOKEN: ${{ ##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## }}
run: |
gh api /PATH>>
 
 
+<<$ sudo ufw enable>>
+<<$ man programs_name>>
+<<$ sudo dnf install certbot python3-certbot-apache>>
+<<$ sudo certbot --apache>>
+<<$ sudo certbot renew --dry-run
+Now, to automate the renewal of the certificate by the script, edit the crontab.
+
+$ crontab -e
+Specify the cron job shown and save the changes.
+
+0 * * * * /usr/sbin/certbot-auto renew>>
+
+
+<<gpg --full-generate-key>>
+If you are not on version 2.1.17 or greater, the gpg --full-generate-key command doesn't work. Paste the text below and skip to step 6.
+
+<Shell>
+
+
+<<terminal>>
+
+<# cat file.txt>
+
+
+<<example>>
+
+<<<<# cat file1.txt file2.txt file3.txt>>>>>
+
+<<ssh -T git@github.com in the terminal:
+
+$ ssh -T git@github.com
+# Attempt to SSH in to github
+> Hi USERNAME! You've successfully authenticated, but GitHub does not provide
+> shell access.>>
+<<ssh -T git@github.com once more. If all is well, you'll get back the same prompt as you did locally.
+
+If you're unsure if your local key is being used, you can also inspect the SSH_AUTH_SOCK variable on your server:
+
+$ echo "$SSH_AUTH_SOCK"
+# Print out the SSH_AUTH_SOCK variable
+> /tmp/ssh-4hNGMk8AZX/agent.79453
+If the variable is not set, it means that agent forwarding is not working:
+
+$ echo "$SSH_AUTH_SOCK"
+# Print out the SSH_AUTH_SOCK variable
+> [No output]
+$ ssh -T git@github.com
+# Try to SSH to github
+> Permission denied (publickey).
+Troubleshooting SSH agent forwarding
+
+Here are some things to look out for when troubleshooting SSH agent forwarding.
+
+You must be using an SSH URL to check out code
+
+SSH forwarding only works with SSH URLs, not HTTP(s) URLs. Check the .git/config file on your server and ensure the URL is an SSH-style URL like below:
+
+[remote "origin"]
url = git@github.com:YOUR_ACCOUNT/YOUR_PROJECT.git
fetch = +refs/heads/:refs/remotes/origin/
+Your SSH keys must work locally
 
+Before you can make your keys work through agent forwarding, they must work locally first. Our guide on generating SSH keys can help you set up your SSH keys locally.
+
+Your system must allow SSH agent forwarding
+
+Sometimes, system configurations disallow SSH agent forwarding. You can check if a system configuration file is being used by entering the following command in the terminal:
+
+$ ssh -v URL
+# Connect to the specified URL with verbose debug output
+> OpenSSH_8.1p1, LibreSSL 2.7.3
+> debug1: Reading configuration data /Users/YOU/.ssh/config
+> debug1: Applying options for example.com
+> debug1: Reading configuration data /etc/ssh_config
+> debug1: Applying options for *
+$ exit
+# Returns to your local command prompt
+In the example above, the file ~/.ssh/config is loaded first, then /etc/ssh_config is read. We can inspect that file to see if it's overriding our options by running the following commands:
+
+$ cat /etc/ssh_config
+# Print out the /etc/ssh_config file
+> Host *
+> SendEnv LANG LC_*
+> ForwardAgent no
+In this example, our /etc/ssh_config file specifically says ForwardAgent no, which is a way to block agent forwarding. Deleting this line from the file should get agent forwarding working once more.
+
+Your server must allow SSH agent forwarding on inbound connections
+
+Agent forwarding may also be blocked on your server. You can check that agent forwarding is permitted by SSHing into the server and running sshd_config. The output from this command should indicate that AllowAgentForwarding is set.
+
+Your local ssh-agent must be running
+
+On most computers, the operating system automatically launches ssh-agent for you. On Windows, however, you need to do this manually. We have a guide on how to start ssh-agent whenever you open Git Bash.
+
+To verify that ssh-agent is running on your computer, type the following command in the terminal:
+
+$ echo "$SSH_AUTH_SOCK"
+# Print out the SSH_AUTH_SOCK variable
+> /tmp/launch-kNSlgU/Listeners
+Your key must be available to ssh-agent
+
+You can check that your key is visible to ssh-agent by running the following command:
+
+ssh-add -L
+If the command says that no identity is available, you'll need to add your key:
+
+ssh-add YOUR-KEY
+Tip
+
+On macOS, ssh-agent will "forget" this key, once it gets restarted during reboots. But you can import your SSH keys into Keychain using this command:
+
+ssh-add --apple-use-keychain YOUR-KEY
+Note
+
+The --apple-use-keychain option stores the passphrase in your keychain for you when you add an SSH key to the ssh-agent. If you chose not to add a passphrase to your key, run the command without the --apple-use-keychain option.
+
+The --apple-use-keychain option is in Apple's standard version of ssh-add. In macOS versions prior to Monterey (12.0), the --apple-use-keychain and --apple-load-keychain flags used the syntax -K and -A, respectively.
+
+If you don't have Apple's standard version of ssh-add installed, you may receive an error. For more information, see Error: ssh-add: illegal option -- apple-use-keychain.
+
+If you continue to be prompted for your passphrase, you may need to add the command to your ~/.zshrc file (or your ~/.bashrc file for bash).>>
+<<$ ssh-keygen -p -f ~/.ssh/id_ed25519
+> Enter old passphrase: [Type old passphrase]
+> Key has comment 'your_email@example.com'
+> Enter new passphrase (empty for no passphrase): [Type new passphrase]
+> Enter same passphrase again: [Repeat the new passphrase]
+> Your identification has been saved with the new passphrase.>>
+<<ssh-add command, and not an application installed by macports, homebrew, or some other external source.
+
+Start the ssh-agent in the background.
+
+$ eval "$(ssh-agent -s)"
+> Agent pid 59566
+Depending on your environment, you may need to use a different command. For example, you may need to use root access by running sudo -s -H before starting the ssh-agent, or you may need to use exec ssh-agent bash or exec ssh-agent zsh to run the ssh-agent.
+
+If you're using macOS Sierra 10.12.2 or later, you will need to modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain.
+
+First, check to see if your ~/.ssh/config file exists in the default location.
+
+$ open ~/.ssh/config
+> The file /Users/YOU/.ssh/config does not exist.
+If the file doesn't exist, create the file.
+
+touch ~/.ssh/config
+Open your ~/.ssh/config file, then modify the file to contain the following lines. If your SSH key file has a different name or path than the example code, modify the filename or path to match your current setup.
+
+Text
+Host GitHub · Build and ship software on a single, collaborative platform
AddKeysToAgent yes
UseKeychain yes
IdentityFile ~/.ssh/id_ed25519
+Note
 
+If you chose not to add a passphrase to your key, you should omit the UseKeychain line.
+If you see a Bad configuration option: usekeychain error, add an additional line to the configuration's' Host *.github.com section.
+Text
+Host GitHub · Build and ship software on a single, collaborative platform
IgnoreUnknown UseKeychain
+Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file.
 
+ssh-add --apple-use-keychain ~/.ssh/id_ed25519
+Note
+
+The --apple-use-keychain option stores the passphrase in your keychain for you when you add an SSH key to the ssh-agent. If you chose not to add a passphrase to your key, run the command without the --apple-use-keychain option.
+
+The --apple-use-keychain option is in Apple's standard version of ssh-add. In macOS versions prior to Monterey (12.0), the --apple-use-keychain and --apple-load-keychain flags used the syntax -K and -A, respectively.
+
+If you don't have Apple's standard version of ssh-add installed, you may receive an error. For more information, see Error: ssh-add: illegal option -- apple-use-keychain.
+
+If you continue to be prompted for your passphrase, you may need to add the command to your ~/.zshrc file (or your ~/.bashrc file for bash).
+Add the SSH public key to your account on GitHub. For more information, see Adding a new SSH key to your GitHub account.
+
+Generating a new SSH key for a hardware security key
+
+If you are using macOS or Linux, you may need to update your SSH client or install a new SSH client prior to generating a new SSH key. For more information, see Error: Unknown key type.
+
+Insert your hardware security key into your computer.
+
+Open Terminal.
+
+Paste the text below, replacing the email address in the example with the email address associated with your GitHub account.
+
+ssh-keygen -t ed25519-sk -C "your_email@example.com"
+Note
+
+If the command fails and you receive the error invalid format or feature not supported, you may be using a hardware security key that does not support the Ed25519 algorithm. Enter the following command instead.
+
+ssh-keygen -t ecdsa-sk -C "your_email@example.com"
+When you are prompted, touch the button on your hardware security key.
+
+When you are prompted to "Enter a file in which to save the key," press Enter to accept the default file location.
+
+> Enter a file in which to save the key (/Users/YOU/.ssh/id_ed25519_sk): [Press enter]
+When you are prompted to type a passphrase, press Enter.
+
+> Enter passphrase (empty for no passphrase): [Type a passphrase]
+> Enter same passphrase again: [Type passphrase again]>>
+
+<<ssh-keygen -t ed25519 -C "mibnumber001k@gmail.com"
+Note
+
+If you are using a legacy system that doesn't support the Ed25519 algorithm, use:
+
+ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
+This creates a new SSH key, using the provided email as a label.
+
+> Generating public/private ALGORITHM key pair.
+When you're prompted to "Enter a file in which to save the key", you can press Enter to accept the default file location. Please note that if you created SSH keys previously, ssh-keygen may ask you to rewrite another key, in which case we recommend creating a custom-named SSH key. To do so, type the default file location and replace id_ALGORITHM with your custom key name.
+
+> Enter a file in which to save the key (/Users/YOU/.ssh/id_ALGORITHM): [Press enter]
+At the prompt, type a secure passphrase. For more information, see Working with SSH key passphrases.
+
+> Enter passphrase (empty for no passphrase): [Type a passphrase]
+> Enter same passphrase again: [Type passphrase again]
+Adding your SSH key to the ssh-agent
+
+Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key. When adding your SSH key to the agent, use the default macOS ssh-add command, and not an application installed by macports, homebrew, or some other external source.
+
+Start the ssh-agent in the background.
+
+$ eval "$(ssh-agent -s)"
+> Agent pid 59566
+
+<<gpg --default-new-key-algo rsa4096 --gen-key>>
+
+<<gpg --list-secret-keys --keyid-format=long>>
+<<$ gpg --list-secret-keys --keyid-format=long
+/Users/hubot/.gnupg/secring.gpg
+------------------------------------
+sec 4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
+uid Hubot hubot@example.com
+ssb 4096R/4BB6D45482678BE3 2016-03-10
+>>
+
+<< gpg --armor --export 3AA5C34371567BD2
+# Prints the GPG key ID, in ASCII armor format>>
+
+<<<--gpg-sign, unset this configuration so the default format of openpgp will be used.
+
+git config --global --unset gpg.format
+Use the gpg --list-secret-keys --keyid-format=long command to list the long form of the GPG keys for which you have both a public and private key. A private key is required for signing commits or tags.
+
+Shell
+gpg --list-secret-keys --keyid-format=long
+Note
+
+Some GPG installations on Linux may require you to use gpg2 --list-keys --keyid-format LONG to view a list of your existing keys instead. In this case you will also need to configure Git to use gpg2 by running git config --global gpg.program gpg2.
+From the list of GPG keys, copy the long form of the GPG key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:
+
+Shell
+$ gpg --list-secret-keys --keyid-format=long
+/Users/hubot/.gnupg/secring.gpg
+------------------------------------
+sec 4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
+uid Hubot hubot@example.com
+ssb 4096R/4BB6D45482678BE3 2016-03-10
+To set your primary GPG signing key in Git, paste the text below, substituting in the GPG primary key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:
+
+git config --global user.signingkey 3AA5C34371567BD2
+Alternatively, you may want to use a subkey. In this example, the GPG subkey ID is 4BB6D45482678BE3:
+
+git config --global user.signingkey 4BB6D45482678BE3
+If you use multiple keys and subkeys, then you should append an exclamation mark ! to the key to tell git that this is your preferred key. Sometimes you may need to escape the exclamation mark with a back slash: \!.
+
+Optionally, to configure Git to sign all commits and tags by default, enter the following command:
+
+git config --global commit.gpgsign true
+git config --global tag.gpgSign true
+For more information, see Signing commits.
+
+To add your GPG key to your .bashrc startup file, run the following command:
+
+[ -f ~/.bashrc ] && echo -e '\nexport GPG_TTY=$(tty)' >> ~/.bashrc>>>
+
+<< git config --global gpg.format ssh
+To set your SSH signing key in Git, paste the text below, substituting /PATH/TO/.SSH/KEY.PUB with the path to the public key you'd like to use.
+
+git config --global user.signingkey /PATH/TO/.SSH/KEY.PUB>>
+
+<< $ cat ~/.ssh/id_ed25519.pub
+# Then select and copy the contents of the id_ed25519.pub file
+# displayed in the terminal to your clipboard>>
+
+<<<>>> from cryptography.hazmat.primitives import hashes
+>>> from cryptography.hazmat.primitives.asymmetric import dh
+>>> from cryptography.hazmat.primitives.kdf.hkdf import HKDF
+>>> # Generate some parameters. These can be reused.
+>>> parameters = dh.generate_parameters(generator=2, key_size=2048)
+>>> # Generate a private key for use in the exchange.
+>>> server_private_key = parameters.generate_private_key()
+>>> # In a real handshake the peer is a remote client. For this
+>>> # example we'll generate another local private key though. Note that in
+>>> # a DH handshake both peers must agree on a common set of parameters.
+>>> peer_private_key = parameters.generate_private_key()
+>>> shared_key = server_private_key.exchange(peer_private_key.public_key())
+>>> # Perform key derivation.
+>>> derived_key = HKDF(
+... algorithm=hashes.SHA256(),
+... length=32,
+... salt=None,
+... info=b'handshake data',
+... ).derive(shared_key)
+>>> # And now we can demonstrate that the handshake performed in the
+>>> # opposite direction gives the same final value
+>>> same_shared_key = peer_private_key.exchange(
+... server_private_key.public_key()
+... )
+>>> same_derived_key = HKDF(
+... algorithm=hashes.SHA256(),
+... length=32,
+... salt=None,
+... info=b'handshake data',
+... ).derive(same_shared_key)
+>>> derived_key == same_derived_key
+DHE (or EDH), the ephemeral form of this exchange, is strongly preferred over simple DH and provides forward secrecy when used. You must generate a new private key using generate_private_key() for each exchange() when performing an DHE key exchange. An example of the ephemeral form:
+
+>>> from cryptography.hazmat.primitives import hashes
+>>> from cryptography.hazmat.primitives.asymmetric import dh
+>>> from cryptography.hazmat.primitives.kdf.hkdf import HKDF
+>>> # Generate some parameters. These can be reused.
+>>> parameters = dh.generate_parameters(generator=2, key_size=2048)
+>>> # Generate a private key for use in the exchange.
+>>> private_key = parameters.generate_private_key()
+>>> # In a real handshake the peer_public_key will be received from the
+>>> # other party. For this example we'll generate another private key and
+>>> # get a public key from that. Note that in a DH handshake both peers
+>>> # must agree on a common set of parameters.
+>>> peer_public_key = parameters.generate_private_key().public_key()
+>>> shared_key = private_key.exchange(peer_public_key)
+>>> # Perform key derivation.
+>>> derived_key = HKDF(
+... algorithm=hashes.SHA256(),
+... length=32,
+... salt=None,
+... info=b'handshake data',
+... ).derive(shared_key)
+>>> # For the next handshake we MUST generate another private key, but
+>>> # we can reuse the parameters.
+>>> private_key_2 = parameters.generate_private_key()
+>>> peer_public_key_2 = parameters.generate_private_key().public_key()
+>>> shared_key_2 = private_key_2.exchange(peer_public_key_2)
+>>> derived_key_2 = HKDF(
+... algorithm=hashes.SHA256(),
+... length=32,
+... salt=None,
+... info=b'handshake data',
+... ).derive(shared_key_2)
+To assemble a DHParameters and a DHPublicKey from primitive integers, you must first create the DHParameterNumbers and DHPublicNumbers objects. For example, if p, g, and y are int objects received from a peer:
+
+pn = dh.DHParameterNumbers(p, g)
+parameters = pn.parameters()
+peer_public_numbers = dh.DHPublicNumbers(y, pn)
+peer_public_key = peer_public_numbers.public_key()>>>
+<<<# Key.file
+location:%20/home/linuxbrew%0ANote:%20Homebrew%20is%20pre-installed%20on%20image%20but%20not%20added%20to%20PATH.%0Arun%20the%20eval%20%22$(/home/linuxbrew/.linuxbrew/bin/brew%20shellenv)%22%20command%0Ato%20accomplish%20this.
+
+<<<Location: /home/linuxbrew
+Note: Homebrew is pre-installed on image but not added to PATH.
+run the eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)" command
+to accomplish this.>>
+<<Both Xdebug and PCOV extensions are installed, but only Xdebug is enabled.>>
+<<User: postgres
+PostgreSQL service is disabled by default.
+Use the following command as a part of your job to start the service: 'sudo systemctl start postgresql.service'>>
+<<User: root
+Password: root
+MySQL service is disabled by default.
+Use the following command as a part of your job to start the service: 'sudo systemctl start mysql.service'>>
+<<name: Run commands on different operating systems
+on:
push:
branches: [ main ]
pull_request:
branches: [ main ]
 
+jobs:
Run-npm-on-Ubuntu:
name: Run npm on Ubuntu
runs-on: ubuntu-latest
steps:
```
uses: actions/checkout@v4 ```
```
uses: actions/setup-node@v4 ```
with:
node-version: '14'
```
run: npm help ```
 
Run-PSScriptAnalyzer-on-Windows:
name: Run PSScriptAnalyzer on Windows
runs-on: windows-latest
steps:
```
uses: actions/checkout@v4 ```
```
name: Install PSScriptAnalyzer module ```
shell: pwsh
run: |
Set-PSRepository PSGallery -InstallationPolicy Trusted
Install-Module PSScriptAnalyzer -ErrorAction Stop
```
name: Get list of rules ```
shell: pwsh
run: |
Get-ScriptAnalyzerRule
+>
+><<name: Build on Ubuntu
+on: push
+
+jobs:
build:
runs-on: ubuntu-latest
steps:
```
name: Check out repository code ```
uses: actions/checkout@v4
```
name: Install jq tool ```
run: |
sudo apt-get update
sudo apt-get install jq
+Note
+
+Always run sudo apt-get update before installing a package. In case the apt index is stale, this command fetches and re-indexes any available packages, which helps prevent package installation failures.
+Installing software on macOS runners
+
+The following example demonstrates how to install Brew packages and casks as part of a job.
+
+name: Build on macOS
+on: push
+
+jobs:
build:
runs-on: macos-latest
steps:
```
name: Check out repository code ```
uses: actions/checkout@v4
```
name: Install GitHub CLI ```
run: |
brew update
brew install gh
```
name: Install Microsoft Edge ```
run: |
brew update
brew install --cask microsoft-edge>>>>>>
 
+<<his command:
+
echo scd getinfo reader_list \
| gpg-connect-agent --decode | awk '/^D/ {print $2}'
+--card-timeout n
+This option is deprecated. In GnuPG 2.0, it used to be used for DISCONNECT command to control timing issue. Since DISCONNECT command works synchronously, it has no effect.
 
+--enable-pinpad-varlen
+Please specify this option when the card reader supports variable length input for pinpad (default is no). For known readers (listed in ccid-driver.c and apdu.c), this option is not needed. Note that if your card reader doesnâ€™t supports variable length input but you want to use it, you need to specify your pinpad request on your card.
+
+--disable-pinpad
+Even if a card reader features a pinpad, do not try to use it.
+
+--deny-admin
+This option disables the use of admin class commands for card applications where this is supported. Currently we support it for the OpenPGP card. This option is useful to inhibit accidental access to admin class command which could ultimately lock the card through wrong PIN numbers. Note that GnuPG versions older than 2.0.11 featured an --allow-admin option which was required to use such admin commands. This option has no more effect today because the default is now to allow admin commands.
+
+--disable-application name
+This option disables the use of the card application named name. This is mainly useful for debugging or if a application with lower priority should be used by default.
+
+--application-priority namelist
+This option allows one to change the order in which applications of a card a tried if no specific application was requested. namelist is a space or comma delimited list of application names. Unknown names are simply skipped. Applications not mentioned in the list are put in the former order at the end of the new priority list.
+
+To get the list of current active applications, use
+
gpg-connect-agent 'scd getinfo app_list' /bye
+>>
 
+<<gpg-connect-agent 'help COMMAND' /bye>>
+
+<<used.
+
GENKEY [--no-protection] [--preset] [<cache_nonce>]
+Invokes the key generation process and the server will then inquire on the generation parameters, like:
 
S: INQUIRE KEYPARM
C: D (genkey (rsa (nbits 1024)))
C: END
+The format of the key parameters which depends on the algorithm is of the form:
 
(genkey
(algo
(parameter_name_1 ....)
....
(parameter_name_n ....)))
+If everything succeeds, the server returns the public key in a SPKI like S-Expression like this:
+
(public-key
(rsa
(n <mpi>)
(e <mpi>)))
+Here is an example session:
 
C: GENKEY
S: INQUIRE KEYPARM
C: D (genkey (rsa (nbits 1024)))
C: END
S: D (public-key
S: D (rsa (n 326487324683264) (e 10001)))
S OK key created
+>>
 
+<<2.6.6 Importing a Root Certificate
+
+Actually we do not import a Root Cert but provide a way to validate any piece of data by storing its Hash along with a description and an identifier in the PSE. Here is the interface description:
+
ISTRUSTED <fingerprint>
+Check whether the OpenPGP primary key or the X.509 certificate with the given fingerprint is an ultimately trusted key or a trusted Root CA certificate. The fingerprint should be given as a hexstring (without any blanks or colons or whatever in between) and may be left padded with 00 in case of an MD5 fingerprint. GPGAgent will answer with:
 
OK
+The key is in the table of trusted keys.
 
ERR 304 (Not Trusted)
+The key is not in this table.
 
+Gpg needs the entire list of trusted keys to maintain the web of trust; the following command is therefore quite helpful:
+
LISTTRUSTED
+GpgAgent returns a list of trusted keys line by line:
 
S: D 000000001234454556565656677878AF2F1ECCFF P
S: D 340387563485634856435645634856438576457A P
S: D FEDC6532453745367FD83474357495743757435D S
S: OK
+The first item on a line is the hexified fingerprint where MD5 fingerprints are 00 padded to the left and the second item is a flag to indicate the type of key (so that gpg is able to only take care of PGP keys). P = OpenPGP, S = S/MIME. A client should ignore the rest of the line, so that we can extend the format in the future.
 
+Finally a client should be able to mark a key as trusted:
+
MARKTRUSTED fingerprint "P"|"S"
+The server will then pop up a window to ask the user whether she really trusts this key. For this it will probably ask for a text to be displayed like this:
 
S: INQUIRE TRUSTDESC
C: D Do you trust the key with the fingerprint @FPR@
C: D bla fasel blurb.
C: END
S: OK>>
 
 
 
 
+<<_gh-Godstimetravelcorporation-e.scpf-foundation-roblox.fandom.com>>
+
+<<595a2d4e38>>
+
+<<
+1. Create a TXT record in your DNS configuration for the following hostname: _gh-Godstimetravelcorporation-e.scpf-foundation-roblox.fandom.com
+2. Use this code for the value of the TXT record: 595a2d4e38. Please note that the code will expire in 7 days.
+3. Wait until your DNS configuration changes. This could take up to 72 hours to propagate.
+>>
+>>
+<<podman pull registry.opensuse.org/kubevirt/cdi-apiserver:1.61.0 podman pull registry.opensuse.org/kubevirt/cdi-apiserver:1.61.0-1.2 podman pull registry.opensuse.org/kubevirt/cdi-apiserver:1.61.0.9.342>> <<podman pull registry.opensuse.org/kubevirt/cdi-apiserver:1.61.0-1.1>> <obs://build.opensuse.org/openSUSE:Factory/containerfile/0aa2e3c4fc8a6a0c87755acabca779b4-cdi-apiserver-container> <<podman pull registry.opensuse.org/kubevirt/cdi-cloner:1.61.0>>
+
+<<<<PATH>>>>
+
+
+<<query {
viewer {
login
}
+}>>
+<<array.
 
+{
"data": null,
"errors": [
{
"message": "Objects must have selections (field 'nodes' returns Repository but has no selections)",
"locations": [
{
"line": 5,
"column": 8
}
]
}
]
+}
+It's possible you might run into an unexpected error that is not related to the schema. If this happens, the message will include a reference code you can use when reporting the issue:
 
+{
"data": null,
"errors": [
{
"message": "Something went wrong while executing your query. This is most likely a GitHub bug. Please include \\"7571:3FF6:552G94B:69F45B7:5913BBEQ\\" when reporting this issue."
}
]
+}>>
 
+<<Here's a contrived example of a schema that defines interface X and object Y:
+
+interface X {
some_field: String!
other_field: String!
+}
 
+type Y implements X {
some_field: String!
other_field: String!
new_field: String!
+}>>
+<<Query __schema to list all types defined in the schema and get details about each:
 
+query {
__schema {
types {
name
kind
description
fields {
name
}
}
}
+}
+Query __type to get details about any type:
 
+query {
__type(name: "Repository") {
name
kind
description
fields {
name
}
}
+}
+You can also run an introspection query of the schema via a GET request:
 
+curl -H "Authorization: bearer TOKEN" https://api.github.com/graphql
+Note
+
+If you get the response "message": "Bad credentials" or 401 Unauthorized, check that you are using a valid token. If you receive a 403 error with Resource not accessible by personal access token, ensure that your fine-grained personal access token is targeted to the correct resource owner. For example, it must target the organization that owns the repository you are trying to access.
+The results are in JSON, so we recommend pretty-printing them for easier reading and searching. You can use a command-line tool like jq or pipe the results into python -m json.tool for this purpose.
+
+Alternatively, you can pass the idl media type to return the results in IDL format, which is a condensed version of the schema:
+
+$ curl -H "Authorization: bearer TOKEN" -H "Accept: application/vnd.github.v4.idl" \
+https://api.github.com/graphql>>
+<<curl -i --header "Authorization: Bearer YOUR-TOKEN" https://api.github.com/user
+you'll get a response that includes the node_id of the authenticated user:
+
+{
"login": "octocat",
"id": 1,
"avatar_url": "https://github.com/images/error/octocat_happy.gif",
"gravatar_id": "",
"url": "https://api.github.com/users/octocat",
"html_url": "octocat - Overview ",
"followers_url": "https://api.github.com/users/octocat/followers",
"following_url": "https://api.github.com/users/octocat/following{/other_user}",
"gists_url": "https://api.github.com/users/octocat/gists{/gist_id}",
"starred_url": "https://api.github.com/users/octocat/starred{/owner}{/repo}",
"subscriptions_url": "https://api.github.com/users/octocat/subscriptions",
"organizations_url": "https://api.github.com/users/octocat/orgs",
"repos_url": "https://api.github.com/users/octocat/repos",
"events_url": "https://api.github.com/users/octocat/events{/privacy}",
"received_events_url": "https://api.github.com/users/octocat/received_events",
"type": "User",
"site_admin": false,
"name": "monalisa octocat",
"company": "GitHub",
"blog": "https://github.com/blog",
"location": "San Francisco",
"email": "octocat@github.com",
"hireable": false,
"bio": "There once was...",
"public_repos": 2,
"public_gists": 1,
"followers": 20,
"following": 0,
"created_at": "2008-01-14T04:33:35Z",
"updated_at": "2008-01-14T04:33:35Z",
"private_gists": 81,
"total_private_repos": 100,
"owned_private_repos": 100,
"disk_usage": 10000,
"collaborators": 8,
"two_factor_authentication": true,
"plan": {
"name": "Medium",
"space": 400,
"private_repos": 20,
"collaborators": 0
},
"node_id": "MDQ6VXNlcjU4MzIzMQ=="
+}
+2. Find the object type in GraphQL
 
+In this example, the node_id value is MDQ6VXNlcjU4MzIzMQ==. You can use this value to query the same object in GraphQL.
+
+You'll need to know the object's type first, though. You can check the type with a simple GraphQL query:
+
+query {
node(id:"MDQ6VXNlcjU4MzIzMQ==") {
__typename
}
+}
+This type of queryâ€”that is, finding the node by IDâ€”is known as a "direct node lookup."
 
+When you run this query, you'll see that the __typename is User.
+
+3. Do a direct node lookup in GraphQL
+
+Once you've confirmed the type, you can use an inline fragment to access the object by its ID and return additional data. In this example, we define the fields on User that we'd like to query:
+
+query {
node(id:"MDQ6VXNlcjU4MzIzMQ==") {
... on User {
name
login
}
}
+}>>>
+<token:##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##>
+<<curl -L \
-H "Accept: application/vnd.github+json" \
-H "Authorization: Bearer <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>" \
-H "X-GitHub-Api-Version: 2022-11-28" \
https://api.github.com/user
+<<curl -L \
-X PATCH \
-H "Accept: application/vnd.github+json" \
-H "Authorization: Bearer <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>" \
-H "X-GitHub-Api-Version: 2022-11-28" \
https://api.github.com/user \
-d '{"blog":"https://github.com/blog","name":"monalisa octocat"}'>>
 
+<<http://api.github.com >> with your enterprise's dedicated subdomain at <<api.SUBDOMAIN.ghe.com>>
+
+<<name: Context testing
+on: push
+
+jobs:
dump_contexts_to_log:
runs-on: ubuntu-latest
steps:
```
name: Dump GitHub context ```
env:
GITHUB_CONTEXT: ${{ toJson(github) }}
run: echo "$GITHUB_CONTEXT"
```
name: Dump job context ```
env:
JOB_CONTEXT: ${{ toJson(job) }}
run: echo "$JOB_CONTEXT"
```
name: Dump steps context ```
env:
STEPS_CONTEXT: ${{ toJson(steps) }}
run: echo "$STEPS_CONTEXT"
```
name: Dump runner context ```
env:
RUNNER_CONTEXT: ${{ toJson(runner) }}
run: echo "$RUNNER_CONTEXT"
```
name: Dump strategy context ```
env:
STRATEGY_CONTEXT: ${{ toJson(strategy) }}
run: echo "$STRATEGY_CONTEXT"
```
name: Dump matrix context ```
env:
MATRIX_CONTEXT: ${{ toJson(matrix) }}
run: echo "$MATRIX_CONTEXT"
+>>
+jobs:
use_api:
runs-on: ubuntu-latest
permissions: {}
steps:
```
env: ```
GH_TOKEN: ${{ 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 }}
run: |
curl --request GET \\
--url "<https://api.github.com/PATH>" \\
--header "Authorization: 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"
 
 
+<curl> <<GITHUB_TOKEN>> as an environment variable, and use the <run> keyword to execute the GitHub CLI <api> subcommand. For more information about the run keyword, see Workflow syntax for GitHub Actions.
+
+In the following example workflow, replace PATH with the path of the endpoint. For more information about the path, see Getting started with the REST API.
+
+<<jobs:
use_api:
runs-on: ubuntu-latest
permissions: {}
steps:
```
env: ```
GH_TOKEN: ${{ ##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## }}
run: |
gh api /PATH>>
 
 
+<<$ sudo ufw enable>>
+<<$ man programs_name>>
+<<$ sudo dnf install certbot python3-certbot-apache>>
+<<$ sudo certbot --apache>>
+<<$ sudo certbot renew --dry-run
+Now, to automate the renewal of the certificate by the script, edit the crontab.
+
+$ crontab -e
+Specify the cron job shown and save the changes.
+
+0 * * * * /usr/sbin/certbot-auto renew>>
+
+
+<<gpg --full-generate-key>>
+If you are not on version 2.1.17 or greater, the gpg --full-generate-key command doesn't work. Paste the text below and skip to step 6.
+
+<Shell>
+
+
+<<terminal>>
+
+<# cat file.txt>
+
+
+<<example>>
+
+<<<<# cat file1.txt file2.txt file3.txt>>>>>
+
+<<ssh -T git@github.com in the terminal:
+
+$ ssh -T git@github.com
+# Attempt to SSH in to github
+> Hi USERNAME! You've successfully authenticated, but GitHub does not provide
+> shell access.>>
+<<ssh -T git@github.com once more. If all is well, you'll get back the same prompt as you did locally.
+
+If you're unsure if your local key is being used, you can also inspect the SSH_AUTH_SOCK variable on your server:
+
+$ echo "$SSH_AUTH_SOCK"
+# Print out the SSH_AUTH_SOCK variable
+> /tmp/ssh-4hNGMk8AZX/agent.79453
+If the variable is not set, it means that agent forwarding is not working:
+
+$ echo "$SSH_AUTH_SOCK"
+# Print out the SSH_AUTH_SOCK variable
+> [No output]
+$ ssh -T git@github.com
+# Try to SSH to github
+> Permission denied (publickey).
+Troubleshooting SSH agent forwarding
+
+Here are some things to look out for when troubleshooting SSH agent forwarding.
+
+You must be using an SSH URL to check out code
+
+SSH forwarding only works with SSH URLs, not HTTP(s) URLs. Check the .git/config file on your server and ensure the URL is an SSH-style URL like below:
+
+[remote "origin"]
url = git@github.com:YOUR_ACCOUNT/YOUR_PROJECT.git
fetch = +refs/heads/:refs/remotes/origin/
+Your SSH keys must work locally
 
+Before you can make your keys work through agent forwarding, they must work locally first. Our guide on generating SSH keys can help you set up your SSH keys locally.
+
+Your system must allow SSH agent forwarding
+
+Sometimes, system configurations disallow SSH agent forwarding. You can check if a system configuration file is being used by entering the following command in the terminal:
+
+$ ssh -v URL
+# Connect to the specified URL with verbose debug output
+> OpenSSH_8.1p1, LibreSSL 2.7.3
+> debug1: Reading configuration data /Users/YOU/.ssh/config
+> debug1: Applying options for example.com
+> debug1: Reading configuration data /etc/ssh_config
+> debug1: Applying options for *
+$ exit
+# Returns to your local command prompt
+In the example above, the file ~/.ssh/config is loaded first, then /etc/ssh_config is read. We can inspect that file to see if it's overriding our options by running the following commands:
+
+$ cat /etc/ssh_config
+# Print out the /etc/ssh_config file
+> Host *
+> SendEnv LANG LC_*
+> ForwardAgent no
+In this example, our /etc/ssh_config file specifically says ForwardAgent no, which is a way to block agent forwarding. Deleting this line from the file should get agent forwarding working once more.
+
+Your server must allow SSH agent forwarding on inbound connections
+
+Agent forwarding may also be blocked on your server. You can check that agent forwarding is permitted by SSHing into the server and running sshd_config. The output from this command should indicate that AllowAgentForwarding is set.
+
+Your local ssh-agent must be running
+
+On most computers, the operating system automatically launches ssh-agent for you. On Windows, however, you need to do this manually. We have a guide on how to start ssh-agent whenever you open Git Bash.
+
+To verify that ssh-agent is running on your computer, type the following command in the terminal:
+
+$ echo "$SSH_AUTH_SOCK"
+# Print out the SSH_AUTH_SOCK variable
+> /tmp/launch-kNSlgU/Listeners
+Your key must be available to ssh-agent
+
+You can check that your key is visible to ssh-agent by running the following command:
+
+ssh-add -L
+If the command says that no identity is available, you'll need to add your key:
+
+ssh-add YOUR-KEY
+Tip
+
+On macOS, ssh-agent will "forget" this key, once it gets restarted during reboots. But you can import your SSH keys into Keychain using this command:
+
+ssh-add --apple-use-keychain YOUR-KEY
+Note
+
+The --apple-use-keychain option stores the passphrase in your keychain for you when you add an SSH key to the ssh-agent. If you chose not to add a passphrase to your key, run the command without the --apple-use-keychain option.
+
+The --apple-use-keychain option is in Apple's standard version of ssh-add. In macOS versions prior to Monterey (12.0), the --apple-use-keychain and --apple-load-keychain flags used the syntax -K and -A, respectively.
+
+If you don't have Apple's standard version of ssh-add installed, you may receive an error. For more information, see Error: ssh-add: illegal option -- apple-use-keychain.
+
+If you continue to be prompted for your passphrase, you may need to add the command to your ~/.zshrc file (or your ~/.bashrc file for bash).>>
+<<$ ssh-keygen -p -f ~/.ssh/id_ed25519
+> Enter old passphrase: [Type old passphrase]
+> Key has comment 'your_email@example.com'
+> Enter new passphrase (empty for no passphrase): [Type new passphrase]
+> Enter same passphrase again: [Repeat the new passphrase]
+> Your identification has been saved with the new passphrase.>>
+<<ssh-add command, and not an application installed by macports, homebrew, or some other external source.
+
+Start the ssh-agent in the background.
+
+$ eval "$(ssh-agent -s)"
+> Agent pid 59566
+Depending on your environment, you may need to use a different command. For example, you may need to use root access by running sudo -s -H before starting the ssh-agent, or you may need to use exec ssh-agent bash or exec ssh-agent zsh to run the ssh-agent.
+
+If you're using macOS Sierra 10.12.2 or later, you will need to modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain.
+
+First, check to see if your ~/.ssh/config file exists in the default location.
+
+$ open ~/.ssh/config
+> The file /Users/YOU/.ssh/config does not exist.
+If the file doesn't exist, create the file.
+
+touch ~/.ssh/config
+Open your ~/.ssh/config file, then modify the file to contain the following lines. If your SSH key file has a different name or path than the example code, modify the filename or path to match your current setup.
+
+Text
+Host GitHub · Build and ship software on a single, collaborative platform
AddKeysToAgent yes
UseKeychain yes
IdentityFile ~/.ssh/id_ed25519
+Note
 
+If you chose not to add a passphrase to your key, you should omit the UseKeychain line.
+If you see a Bad configuration option: usekeychain error, add an additional line to the configuration's' Host *.github.com section.
+Text
+Host GitHub · Build and ship software on a single, collaborative platform
IgnoreUnknown UseKeychain
+Add your SSH private key to the ssh-agent and store your passphrase in the keychain. If you created your key with a different name, or if you are adding an existing key that has a different name, replace id_ed25519 in the command with the name of your private key file.
 
+ssh-add --apple-use-keychain ~/.ssh/id_ed25519
+Note
+
+The --apple-use-keychain option stores the passphrase in your keychain for you when you add an SSH key to the ssh-agent. If you chose not to add a passphrase to your key, run the command without the --apple-use-keychain option.
+
+The --apple-use-keychain option is in Apple's standard version of ssh-add. In macOS versions prior to Monterey (12.0), the --apple-use-keychain and --apple-load-keychain flags used the syntax -K and -A, respectively.
+
+If you don't have Apple's standard version of ssh-add installed, you may receive an error. For more information, see Error: ssh-add: illegal option -- apple-use-keychain.
+
+If you continue to be prompted for your passphrase, you may need to add the command to your ~/.zshrc file (or your ~/.bashrc file for bash).
+Add the SSH public key to your account on GitHub. For more information, see Adding a new SSH key to your GitHub account.
+
+Generating a new SSH key for a hardware security key
+
+If you are using macOS or Linux, you may need to update your SSH client or install a new SSH client prior to generating a new SSH key. For more information, see Error: Unknown key type.
+
+Insert your hardware security key into your computer.
+
+Open Terminal.
+
+Paste the text below, replacing the email address in the example with the email address associated with your GitHub account.
+
+ssh-keygen -t ed25519-sk -C "your_email@example.com"
+Note
+
+If the command fails and you receive the error invalid format or feature not supported, you may be using a hardware security key that does not support the Ed25519 algorithm. Enter the following command instead.
+
+ssh-keygen -t ecdsa-sk -C "your_email@example.com"
+When you are prompted, touch the button on your hardware security key.
+
+When you are prompted to "Enter a file in which to save the key," press Enter to accept the default file location.
+
+> Enter a file in which to save the key (/Users/YOU/.ssh/id_ed25519_sk): [Press enter]
+When you are prompted to type a passphrase, press Enter.
+
+> Enter passphrase (empty for no passphrase): [Type a passphrase]
+> Enter same passphrase again: [Type passphrase again]>>
+
+<<ssh-keygen -t ed25519 -C "mibnumber001k@gmail.com"
+Note
+
+If you are using a legacy system that doesn't support the Ed25519 algorithm, use:
+
+ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
+This creates a new SSH key, using the provided email as a label.
+
+> Generating public/private ALGORITHM key pair.
+When you're prompted to "Enter a file in which to save the key", you can press Enter to accept the default file location. Please note that if you created SSH keys previously, ssh-keygen may ask you to rewrite another key, in which case we recommend creating a custom-named SSH key. To do so, type the default file location and replace id_ALGORITHM with your custom key name.
+
+> Enter a file in which to save the key (/Users/YOU/.ssh/id_ALGORITHM): [Press enter]
+At the prompt, type a secure passphrase. For more information, see Working with SSH key passphrases.
+
+> Enter passphrase (empty for no passphrase): [Type a passphrase]
+> Enter same passphrase again: [Type passphrase again]
+Adding your SSH key to the ssh-agent
+
+Before adding a new SSH key to the ssh-agent to manage your keys, you should have checked for existing SSH keys and generated a new SSH key. When adding your SSH key to the agent, use the default macOS ssh-add command, and not an application installed by macports, homebrew, or some other external source.
+
+Start the ssh-agent in the background.
+
+$ eval "$(ssh-agent -s)"
+> Agent pid 59566
+
+<<gpg --default-new-key-algo rsa4096 --gen-key>>
+
+<<gpg --list-secret-keys --keyid-format=long>>
+<<$ gpg --list-secret-keys --keyid-format=long
+/Users/hubot/.gnupg/secring.gpg
+------------------------------------
+sec 4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
+uid Hubot hubot@example.com
+ssb 4096R/4BB6D45482678BE3 2016-03-10
+>>
+
+<< gpg --armor --export 3AA5C34371567BD2
+# Prints the GPG key ID, in ASCII armor format>>
+
+<<<--gpg-sign, unset this configuration so the default format of openpgp will be used.
+
+git config --global --unset gpg.format
+Use the gpg --list-secret-keys --keyid-format=long command to list the long form of the GPG keys for which you have both a public and private key. A private key is required for signing commits or tags.
+
+Shell
+gpg --list-secret-keys --keyid-format=long
+Note
+
+Some GPG installations on Linux may require you to use gpg2 --list-keys --keyid-format LONG to view a list of your existing keys instead. In this case you will also need to configure Git to use gpg2 by running git config --global gpg.program gpg2.
+From the list of GPG keys, copy the long form of the GPG key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:
+
+Shell
+$ gpg --list-secret-keys --keyid-format=long
+/Users/hubot/.gnupg/secring.gpg
+------------------------------------
+sec 4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
+uid Hubot hubot@example.com
+ssb 4096R/4BB6D45482678BE3 2016-03-10
+To set your primary GPG signing key in Git, paste the text below, substituting in the GPG primary key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:
+
+git config --global user.signingkey 3AA5C34371567BD2
+Alternatively, you may want to use a subkey. In this example, the GPG subkey ID is 4BB6D45482678BE3:
+
+git config --global user.signingkey 4BB6D45482678BE3
+If you use multiple keys and subkeys, then you should append an exclamation mark ! to the key to tell git that this is your preferred key. Sometimes you may need to escape the exclamation mark with a back slash: \!.
+
+Optionally, to configure Git to sign all commits and tags by default, enter the following command:
+
+git config --global commit.gpgsign true
+git config --global tag.gpgSign true
+For more information, see Signing commits.
+
+To add your GPG key to your .bashrc startup file, run the following command:
+
+[ -f ~/.bashrc ] && echo -e '\nexport GPG_TTY=$(tty)' >> ~/.bashrc>>>
+
+<< git config --global gpg.format ssh
+To set your SSH signing key in Git, paste the text below, substituting /PATH/TO/.SSH/KEY.PUB with the path to the public key you'd like to use.
+
+git config --global user.signingkey /PATH/TO/.SSH/KEY.PUB>>
+
+<< $ cat ~/.ssh/id_ed25519.pub
+# Then select and copy the contents of the id_ed25519.pub file
+# displayed in the terminal to your clipboard>>
+
+<<<>>> from cryptography.hazmat.primitives import hashes
+>>> from cryptography.hazmat.primitives.asymmetric import dh
+>>> from cryptography.hazmat.primitives.kdf.hkdf import HKDF
+>>> # Generate some parameters. These can be reused.
+>>> parameters = dh.generate_parameters(generator=2, key_size=2048)
+>>> # Generate a private key for use in the exchange.
+>>> server_private_key = parameters.generate_private_key()
+>>> # In a real handshake the peer is a remote client. For this
+>>> # example we'll generate another local private key though. Note that in
+>>> # a DH handshake both peers must agree on a common set of parameters.
+>>> peer_private_key = parameters.generate_private_key()
+>>> shared_key = server_private_key.exchange(peer_private_key.public_key())
+>>> # Perform key derivation.
+>>> derived_key = HKDF(
+... algorithm=hashes.SHA256(),
+... length=32,
+... salt=None,
+... info=b'handshake data',
+... ).derive(shared_key)
+>>> # And now we can demonstrate that the handshake performed in the
+>>> # opposite direction gives the same final value
+>>> same_shared_key = peer_private_key.exchange(
+... server_private_key.public_key()
+... )
+>>> same_derived_key = HKDF(
+... algorithm=hashes.SHA256(),
+... length=32,
+... salt=None,
+... info=b'handshake data',
+... ).derive(same_shared_key)
+>>> derived_key == same_derived_key
+DHE (or EDH), the ephemeral form of this exchange, is strongly preferred over simple DH and provides forward secrecy when used. You must generate a new private key using generate_private_key() for each exchange() when performing an DHE key exchange. An example of the ephemeral form:
+
+>>> from cryptography.hazmat.primitives import hashes
+>>> from cryptography.hazmat.primitives.asymmetric import dh
+>>> from cryptography.hazmat.primitives.kdf.hkdf import HKDF
+>>> # Generate some parameters. These can be reused.
+>>> parameters = dh.generate_parameters(generator=2, key_size=2048)
+>>> # Generate a private key for use in the exchange.
+>>> private_key = parameters.generate_private_key()
+>>> # In a real handshake the peer_public_key will be received from the
+>>> # other party. For this example we'll generate another private key and
+>>> # get a public key from that. Note that in a DH handshake both peers
+>>> # must agree on a common set of parameters.
+>>> peer_public_key = parameters.generate_private_key().public_key()
+>>> shared_key = private_key.exchange(peer_public_key)
+>>> # Perform key derivation.
+>>> derived_key = HKDF(
+... algorithm=hashes.SHA256(),
+... length=32,
+... salt=None,
+... info=b'handshake data',
+... ).derive(shared_key)
+>>> # For the next handshake we MUST generate another private key, but
+>>> # we can reuse the parameters.
+>>> private_key_2 = parameters.generate_private_key()
+>>> peer_public_key_2 = parameters.generate_private_key().public_key()
+>>> shared_key_2 = private_key_2.exchange(peer_public_key_2)
+>>> derived_key_2 = HKDF(
+... algorithm=hashes.SHA256(),
+... length=32,
+... salt=None,
+... info=b'handshake data',
+... ).derive(shared_key_2)
+To assemble a DHParameters and a DHPublicKey from primitive integers, you must first create the DHParameterNumbers and DHPublicNumbers objects. For example, if p, g, and y are int objects received from a peer:
+
+pn = dh.DHParameterNumbers(p, g)
+parameters = pn.parameters()
+peer_public_numbers = dh.DHPublicNumbers(y, pn)
+peer_public_key = peer_public_numbers.public_key()>>>
+<<<# Key.file
+location:%20/home/linuxbrew%0ANote:%20Homebrew%20is%20pre-installed%20on%20image%20but%20not%20added%20to%20PATH.%0Arun%20the%20eval%20%22$(/home/linuxbrew/.linuxbrew/bin/brew%20shellenv)%22%20command%0Ato%20accomplish%20this.
+
+<<<Location: /home/linuxbrew
+Note: Homebrew is pre-installed on image but not added to PATH.
+run the eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)" command
+to accomplish this.>>
+<<Both Xdebug and PCOV extensions are installed, but only Xdebug is enabled.>>
+<<User: postgres
+PostgreSQL service is disabled by default.
+Use the following command as a part of your job to start the service: 'sudo systemctl start postgresql.service'>>
+<<User: root
+Password: root
+MySQL service is disabled by default.
+Use the following command as a part of your job to start the service: 'sudo systemctl start mysql.service'>>
+<<name: Run commands on different operating systems
+on:
push:
branches: [ main ]
pull_request:
branches: [ main ]
 
+jobs:
Run-npm-on-Ubuntu:
name: Run npm on Ubuntu
runs-on: ubuntu-latest
steps:
```
uses: actions/checkout@v4 ```
```
uses: actions/setup-node@v4 ```
with:
node-version: '14'
```
run: npm help ```
 
Run-PSScriptAnalyzer-on-Windows:
name: Run PSScriptAnalyzer on Windows
runs-on: windows-latest
steps:
```
uses: actions/checkout@v4 ```
```
name: Install PSScriptAnalyzer module ```
shell: pwsh
run: |
Set-PSRepository PSGallery -InstallationPolicy Trusted
Install-Module PSScriptAnalyzer -ErrorAction Stop
```
name: Get list of rules ```
shell: pwsh
run: |
Get-ScriptAnalyzerRule
+>
+><<name: Build on Ubuntu
+on: push
+
+jobs:
build:
runs-on: ubuntu-latest
steps:
```
name: Check out repository code ```
uses: actions/checkout@v4
```
name: Install jq tool ```
run: |
sudo apt-get update
sudo apt-get install jq
+Note
+
+Always run sudo apt-get update before installing a package. In case the apt index is stale, this command fetches and re-indexes any available packages, which helps prevent package installation failures.
+Installing software on macOS runners
+
+The following example demonstrates how to install Brew packages and casks as part of a job.
+
+name: Build on macOS
+on: push
+
+jobs:
build:
runs-on: macos-latest
steps:
```
name: Check out repository code ```
uses: actions/checkout@v4
```
name: Install GitHub CLI ```
run: |
brew update
brew install gh
```
name: Install Microsoft Edge ```
run: |
brew update
brew install --cask microsoft-edge>>>>>>
 
 
 
+<< following git clone command. You would then be prompted to enter your username and password. When prompted for your password, enter your personal access token instead of a password.
+
+$ git clone https://github.com/USERNAME/REPO.gitConnect your Github account 
+Username: YOUR-USERNAME
+Password: YOUR-PERSONAL-ACCESS-TOKEN>>
+<< "features": {
"ghcr.io/devcontainers/features/github-cli:1": {}
+}>>>
+<< $ gh at verify -R cli/cli gh_2.62.0_macOS_arm64.zip
+Loaded digest sha256:fdb77f31b8a6dd23c3fd858758d692a45f7fc76383e37d475bdcae038df92afc for file://gh_2.62.0_macOS_arm64.zip
+Loaded 1 attestation from GitHub API
+âœ“ Verification succeeded!
 
+sha256:fdb77f31b8a6dd23c3fd858758d692a45f7fc76383e37d475bdcae038df92afc was attested by:
+REPO PREDICATE_TYPE WORKFLOW
+cli/cli https://slsa.dev/provenance/v1 .github/workflows/deployment.yml@refs/heads/trunk>>
+<< $ cosign verify-blob-attestation --bundle cli-cli-attestation-3120304.sigstore.json \
--new-bundle-format \\
--certificate-oidc-issuer="<https://token.actions.githubusercontent.com>" \\
--certificate-identity-regexp="^<https://github.com/cli/cli/.github/workflows/deployment.yml@refs/heads/trunk$>" \\
gh_2.62.0_macOS_arm64.zip
+Verified OK>>
+<< $ hub clone rtomayko/tilt
+#=> git clone GitHub - rtomayko/tilt: Generic interface to multiple Ruby template engines 
+
+# or, if you prefer the SSH protocol:
+$ git config --global hub.protocol ssh
+$ hub clone rtomayko/tilt
+#=> git clone git@github.com:rtomayko/tilt.git>>
+
+<< steps:
+- uses: actions/checkout@v2
+
+- name: List open pull requests
run: hub pr list
env:
GITHUB_TOKEN: ${{ ##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## }}>>
<< make install:
 
+git clone \
--config transfer.fsckobjects=false \
--config receive.fsckobjects=false \
--config fetch.fsckobjects=false \
GitHub - mislav/hub: A command-line tool that makes git easier to use with GitHub.
 
+cd hub
+make install prefix=/usr/local>>
+
+
+<<docker pull anishathalye/proof-html:1.1.0>>
+<<gpg --full-generate-key
+# If version < 2.1.17, use:
+gpg --default-new-key-algo rsa4096 --gen-key>>
+<<gpg --list-secret-keys --keyid-format=long>>
+
+<<gpg --armor --export 3AA5C34371567BD2>>
+<<git config --global --unset gpg.format>>
+<<git config --global user.signingkey 3AA5C34371567BD2
+# Or using a subkey
+git config --global user.signingkey 4BB6D45482678BE3>>
+
+<<cat ~/.ssh/id_ed25519.pub>>
+<<git config --global gpg.format ssh
+git config --global user.signingkey /PATH/TO/.SSH/KEY.PUB>>
+<<[ -f ~/.bashrc ] && echo -e '\nexport GPG_TTY=$(tty)' >> ~/.bashrc>>
+
+<<git config --global user.signingkey 3AA5C34371567BD2
+# Or using a subkey
+git config --global user.signingkey 4BB6D45482678BE3>>
+<<gpg --armor --export 3AA5C34371567BD2>>
+<<name: Run commands on different operating systems
+on:
push:
branches: [ main ]
pull_request:
branches: [ main ]
 
+jobs:
Run-npm-on-Ubuntu:
name: Run npm on Ubuntu
runs-on: ubuntu-latest
steps:
```
uses: actions/checkout@v4 ```
```
uses: actions/setup-node@v4 ```
with:
node-version: '14'
```
run: npm help ```
 
Run-PSScriptAnalyzer-on-Windows:
name: Run PSScriptAnalyzer on Windows
runs-on: windows-latest
steps:
```
uses: actions/checkout@v4 ```
```
name: Install PSScriptAnalyzer module ```
shell: pwsh
run: |
Set-PSRepository PSGallery -InstallationPolicy Trusted
Install-Module PSScriptAnalyzer -ErrorAction Stop
```
name: Get list of rules ```
shell: pwsh
run: |
Get-ScriptAnalyzerRule>>
 
 
+<<from cryptography.hazmat.primitives import hashes
+from cryptography.hazmat.primitives.asymmetric import dh
+from cryptography.hazmat.primitives.kdf.hkdf import HKDF
+
+# Generate parameters
+parameters = dh.generate_parameters(generator=2, key_size=2048)
+
+# Generate private keys
+server_private_key = parameters.generate_private_key()
+peer_private_key = parameters.generate_private_key()
+
+# Exchange keys and derive shared key
+shared_key = server_private_key.exchange(peer_private_key.public_key())
+derived_key = HKDF(
algorithm=hashes.SHA256(),
length=32,
salt=None,
info=b'handshake data',
+).derive(shared_key)
 
+# Verify same derived key
+same_shared_key = peer_private_key.exchange(server_private_key.public_key())
+same_derived_key = HKDF(
algorithm=hashes.SHA256(),
length=32,
salt=None,
info=b'handshake data',
+).derive(same_shared_key)
+assert derived_key == same_derived_key>>
location:%20/home/linuxbrew%0ANote:%20Homebrew%20is%20pre-installed%20on%20image%20but%20not%20added%20to%20PATH.%0Arun%20the%20eval%20%22$(/home/linuxbrew/.linuxbrew/bin/brew%20shellenv)%22%20command%0Ato%20accomplish%20this.
<<<<gpg --full-generate-key>>
If you are not on version 2.1.17 or greater, the gpg --full-generate-key command doesn't work. Paste the text below and skip to step 6.

Shell
<<gpg --default-new-key-algo rsa4096 --gen-key>>

<<gpg --list-secret-keys --keyid-format=long>>
<<$ gpg --list-secret-keys --keyid-format=long
/Users/hubot/.gnupg/secring.gpg
------------------------------------
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot <hubot@example.com>
ssb   4096R/4BB6D45482678BE3 2016-03-10
>>

<< gpg --armor --export 3AA5C34371567BD2
# Prints the GPG key ID, in ASCII armor format>>

<<<--gpg-sign, unset this configuration so the default format of openpgp will be used.

git config --global --unset gpg.format
Use the gpg --list-secret-keys --keyid-format=long command to list the long form of the GPG keys for which you have both a public and private key. A private key is required for signing commits or tags.

Shell
gpg --list-secret-keys --keyid-format=long
Note

Some GPG installations on Linux may require you to use gpg2 --list-keys --keyid-format LONG to view a list of your existing keys instead. In this case you will also need to configure Git to use gpg2 by running git config --global gpg.program gpg2.
From the list of GPG keys, copy the long form of the GPG key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:

Shell
$ gpg --list-secret-keys --keyid-format=long
/Users/hubot/.gnupg/secring.gpg
------------------------------------
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot <hubot@example.com>
ssb   4096R/4BB6D45482678BE3 2016-03-10
To set your primary GPG signing key in Git, paste the text below, substituting in the GPG primary key ID you'd like to use. In this example, the GPG key ID is 3AA5C34371567BD2:

git config --global user.signingkey 3AA5C34371567BD2
Alternatively, you may want to use a subkey. In this example, the GPG subkey ID is 4BB6D45482678BE3:

git config --global user.signingkey 4BB6D45482678BE3
If you use multiple keys and subkeys, then you should append an exclamation mark ! to the key to tell git that this is your preferred key. Sometimes you may need to escape the exclamation mark with a back slash: \!.

Optionally, to configure Git to sign all commits and tags by default, enter the following command:

git config --global commit.gpgsign true
git config --global tag.gpgSign true
For more information, see [Signing commits](https://docs.github.com/en/authentication/managing-commit-signature-verification/signing-commits).

To add your GPG key to your .bashrc startup file, run the following command:

[ -f ~/.bashrc ] && echo -e '\nexport GPG_TTY=$(tty)' >> ~/.bashrc>>>

<< git config --global gpg.format ssh
To set your SSH signing key in Git, paste the text below, substituting /PATH/TO/.SSH/KEY.PUB with the path to the public key you'd like to use.

git config --global user.signingkey /PATH/TO/.SSH/KEY.PUB>>

<< $ cat ~/.ssh/id_ed25519.pub
# Then select and copy the contents of the id_ed25519.pub file
# displayed in the terminal to your clipboard>>

<<<>>> from cryptography.hazmat.primitives import hashes
>>> from cryptography.hazmat.primitives.asymmetric import dh
>>> from cryptography.hazmat.primitives.kdf.hkdf import HKDF
>>> # Generate some parameters. These can be reused.
>>> parameters = dh.generate_parameters(generator=2, key_size=2048)
>>> # Generate a private key for use in the exchange.
>>> server_private_key = parameters.generate_private_key()
>>> # In a real handshake the peer is a remote client. For this
>>> # example we'll generate another local private key though. Note that in
>>> # a DH handshake both peers must agree on a common set of parameters.
>>> peer_private_key = parameters.generate_private_key()
>>> shared_key = server_private_key.exchange(peer_private_key.public_key())
>>> # Perform key derivation.
>>> derived_key = HKDF(
...     algorithm=hashes.SHA256(),
...     length=32,
...     salt=None,
...     info=b'handshake data',
... ).derive(shared_key)
>>> # And now we can demonstrate that the handshake performed in the
>>> # opposite direction gives the same final value
>>> same_shared_key = peer_private_key.exchange(
...     server_private_key.public_key()
... )
>>> same_derived_key = HKDF(
...     algorithm=hashes.SHA256(),
...     length=32,
...     salt=None,
...     info=b'handshake data',
... ).derive(same_shared_key)
>>> derived_key == same_derived_key
DHE (or EDH), the ephemeral form of this exchange, is strongly preferred over simple DH and provides [forward secrecy](https://en.wikipedia.org/wiki/Forward_secrecy) when used. You must generate a new private key using [generate_private_key()](https://cryptography.io/en/latest/hazmat/primitives/asymmetric/dh/#cryptography.hazmat.primitives.asymmetric.dh.DHParameters.generate_private_key) for each [exchange()](https://cryptography.io/en/latest/hazmat/primitives/asymmetric/dh/#cryptography.hazmat.primitives.asymmetric.dh.DHPrivateKey.exchange) when performing an DHE key exchange. An example of the ephemeral form:

>>> from cryptography.hazmat.primitives import hashes
>>> from cryptography.hazmat.primitives.asymmetric import dh
>>> from cryptography.hazmat.primitives.kdf.hkdf import HKDF
>>> # Generate some parameters. These can be reused.
>>> parameters = dh.generate_parameters(generator=2, key_size=2048)
>>> # Generate a private key for use in the exchange.
>>> private_key = parameters.generate_private_key()
>>> # In a real handshake the peer_public_key will be received from the
>>> # other party. For this example we'll generate another private key and
>>> # get a public key from that. Note that in a DH handshake both peers
>>> # must agree on a common set of parameters.
>>> peer_public_key = parameters.generate_private_key().public_key()
>>> shared_key = private_key.exchange(peer_public_key)
>>> # Perform key derivation.
>>> derived_key = HKDF(
...     algorithm=hashes.SHA256(),
...     length=32,
...     salt=None,
...     info=b'handshake data',
... ).derive(shared_key)
>>> # For the next handshake we MUST generate another private key, but
>>> # we can reuse the parameters.
>>> private_key_2 = parameters.generate_private_key()
>>> peer_public_key_2 = parameters.generate_private_key().public_key()
>>> shared_key_2 = private_key_2.exchange(peer_public_key_2)
>>> derived_key_2 = HKDF(
...     algorithm=hashes.SHA256(),
...     length=32,
...     salt=None,
...     info=b'handshake data',
... ).derive(shared_key_2)
To assemble a [DHParameters](https://cryptography.io/en/latest/hazmat/primitives/asymmetric/dh/#cryptography.hazmat.primitives.asymmetric.dh.DHParameters) and a [DHPublicKey](https://cryptography.io/en/latest/hazmat/primitives/asymmetric/dh/#cryptography.hazmat.primitives.asymmetric.dh.DHPublicKey) from primitive integers, you must first create the [DHParameterNumbers](https://cryptography.io/en/latest/hazmat/primitives/asymmetric/dh/#cryptography.hazmat.primitives.asymmetric.dh.DHParameterNumbers) and [DHPublicNumbers](https://cryptography.io/en/latest/hazmat/primitives/asymmetric/dh/#cryptography.hazmat.primitives.asymmetric.dh.DHPublicNumbers) objects. For example, if p, g, and y are [int](https://docs.python.org/3/library/functions.html#int) objects received from a peer:

pn = dh.DHParameterNumbers(p, g)
parameters = pn.parameters()
peer_public_numbers = dh.DHPublicNumbers(y, pn)
peer_public_key = peer_public_numbers.public_key()>>>
<<<# Key.file
location:%20/home/linuxbrew%0ANote:%20Homebrew%20is%20pre-installed%20on%20image%20but%20not%20added%20to%20PATH.%0Arun%20the%20eval%20%22$(/home/linuxbrew/.linuxbrew/bin/brew%20shellenv)%22%20command%0Ato%20accomplish%20this.

<<<Location: /home/linuxbrew
Note: Homebrew is pre-installed on image but not added to PATH.
run the eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)" command
to accomplish this.>>
<<Both Xdebug and PCOV extensions are installed, but only Xdebug is enabled.>>
<<User: postgres
PostgreSQL service is disabled by default.
Use the following command as a part of your job to start the service: 'sudo systemctl start postgresql.service'>>
<<User: root
Password: root
MySQL service is disabled by default.
Use the following command as a part of your job to start the service: 'sudo systemctl start mysql.service'>>
<<name: Run commands on different operating systems
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  Run-npm-on-Ubuntu:
    name: Run npm on Ubuntu
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '14'
      - run: npm help

  Run-PSScriptAnalyzer-on-Windows:
    name: Run PSScriptAnalyzer on Windows
    runs-on: windows-latest
    steps:
      - uses: actions/checkout@v4
      - name: Install PSScriptAnalyzer module
        shell: pwsh
        run: |
          Set-PSRepository PSGallery -InstallationPolicy Trusted
          Install-Module PSScriptAnalyzer -ErrorAction Stop
      - name: Get list of rules
        shell: pwsh
        run: |
          Get-ScriptAnalyzerRule
>
><<name: Build on Ubuntu
on: push

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Check out repository code
        uses: actions/checkout@v4
      - name: Install jq tool
        run: |
          sudo apt-get update
          sudo apt-get install jq
Note

Always run sudo apt-get update before installing a package. In case the apt index is stale, this command fetches and re-indexes any available packages, which helps prevent package installation failures.
Installing software on macOS runners

The following example demonstrates how to install Brew packages and casks as part of a job.

name: Build on macOS
on: push

jobs:
  build:
    runs-on: macos-latest
    steps:
      - name: Check out repository code
        uses: actions/checkout@v4
      - name: Install GitHub CLI
        run: |
          brew update
          brew install gh
      - name: Install Microsoft Edge
        run: |
          brew update
          brew install --cask microsoft-edge>>>>>>
