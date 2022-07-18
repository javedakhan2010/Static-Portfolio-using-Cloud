<div>
    <h1>Automate static website deployment from Github to S3 using AWS CodePipeline</h1>
</div>
<p>Automatically deploy changes made to the GitHub repository of the static website to AWS S3. The change you make will be instantly available on live website yourdomain.com.</p>
<p>You don&rsquo;t need to clone the git repository to make changes. You can do it from the github.com website itself. After configuring the pipeline, you don&rsquo;t need to login to AWS. Everything happens automatically under the hood.&nbsp;</p>
<p>You need one of your s3 buckets configured for static web hosting for this deployment&nbsp;</p>
<p>Login to <a href="https://ap-southeast-2.console.aws.amazon.com/console/home" rel="noopener ugc nofollow" target="_blank">AWS console</a> and go to <a href="https://ap-southeast-2.console.aws.amazon.com/codesuite/codepipeline/pipelines" rel="noopener ugc nofollow" target="_blank">CodePipeline</a>.</p>
<figure>
    <div tabindex="0">
        <div><img alt="" src="https://miro.medium.com/max/1400/1*QkpLlnRj71ZPT_HFK27AVw.png" width="700" height="256"></div>
    </div>
</figure>
<p><strong>Important</strong>! Switch to the correct AWS region where your S3 website is created before creating the pipeline.</p>
<p>Click the <strong>Create pipeline&nbsp;</strong>button.</p>
<figure>
    <div tabindex="0">
        <div><img alt="" src="https://miro.medium.com/max/1400/1*4IIu1MmCH23-Udft7vhE8Q.png" width="700" height="405"></div>
    </div>
</figure>
<p>Give the <strong>pipeline&nbsp;</strong>a meaningful name: <em>web-s3-deploy</em><br>Select <strong>New service role</strong>. Give it a meaningful name: <em>web-s3-pipeline-role<br></em>Artifact store: Choose the&nbsp;<strong>Default location</strong> option<br>Bucket: select the s3 bucket which the&nbsp;<strong>static website</strong> is hosted.<br>Hit the <strong>Next&nbsp;</strong>button.</p>
<figure>
    <div tabindex="0">
        <div><img alt="" src="https://miro.medium.com/max/1400/1*nquBH-90U1fNFo-ZlYhB3A.png" width="700" height="322"></div>
    </div>
</figure>
<p>Select the Source provider:&nbsp;<strong>Github</strong>.<br>Click the <strong>Connect to Github&nbsp;</strong>button. Authenticate Authorize AWS CodePipeline to access your Github Repos.</p>
<p>After authentication, select the Repository with your static website files. Select the branch of the repository. <em>I&rsquo;m using a static website noobcod.com for this tutorial.</em></p>
<figure>
    <div tabindex="0">
        <div><img alt="" src="https://miro.medium.com/max/1400/1*eFQhI6JFqnXm1yDQNzRKwg.png" width="700" height="401"></div>
    </div>
</figure>
<p>Select the <strong>Github webhooks (Recommended)</strong> option. <strong>Important!</strong> You need to be the <strong>owner&nbsp;</strong>or an <strong>admin&nbsp;</strong>of the repository to create webhooks.</p>
<p>Hit the <strong>Next</strong> button.</p>
<p>Hit <strong>Skip Build Stage&nbsp;</strong>button. <em>You can use AWS Codebuild to compile typescript or any project that need to build before deploy. We skip this because the repo contains static website contents.</em></p>
<p>Hit the <strong>Skip&nbsp;</strong>button on the prompt.</p>
<figure>
    <div tabindex="0">
        <div><img alt="" src="https://miro.medium.com/max/1400/1*Abvahn_5c-p_Au7CRqlsQA.png" width="700" height="397"></div>
    </div>
</figure>
<p>Deploy provider: Select <strong>Amazon S3</strong><br>Bucket: Select the bucket which configured for the&nbsp;<strong>static website</strong>.<br>Extract file before deploy: You <strong>must check&nbsp;</strong>this because code pipeline compresses the artifact.</p>
<p>No additional configurations needed. Hit the <strong>Next&nbsp;</strong>button.</p>
<p>You can go back and change configuration if you made any mistake at the Review step. Hit the <strong>Create Pipeline</strong> button.</p>
<figure>
    <div tabindex="0">
        <div><img alt="" src="https://miro.medium.com/max/1400/1*gB2TQyTpAzdg1rUNxehfSw.png" width="700" height="381"></div>
    </div>
</figure>
<p>Go to your domain from the web browser. It&rsquo;s now deployed.</p>
<figure>
    <div tabindex="0">
        <div><img alt="" src="https://miro.medium.com/max/1400/1*8YwwxNRanv7Wfhrulpwzmg.png" width="700" height="161"></div>
    </div>
</figure>
<p>Make a change on the repository on Github.com website and hit <strong>Commit</strong> button. Ill change v1 to v2 to get a visible change.</p>
<figure>
    <div tabindex="0">
        <div><img alt="" src="https://miro.medium.com/max/1400/1*hspHHR7mW9-kNGh6kVRksA.png" width="700" height="282"></div>
    </div>
</figure>
<p>Cheers! Changes to your static website now automatically deploy to the live URL instantly.</p>
<figure>
    <div tabindex="0">
        <div><img alt="" src="https://miro.medium.com/max/1400/1*t8_13kEYvBW4lmas5aMioA.png" width="700" height="166"></div>
    </div>
</figure>
<p><br></p>
<p>Cost: This pipeline will cost only $1 per month and charges only if a deployment happened.</p>

<script type="text/javascript" language="javascript">
      var aax_size='728x90';
      var aax_pubname = 'javedkhanvide-21';
      var aax_src='302';
    </script>
    <script type="text/javascript" language="javascript" src="http://c.amazon-adsystem.com/aax2/assoc.js"></script>
