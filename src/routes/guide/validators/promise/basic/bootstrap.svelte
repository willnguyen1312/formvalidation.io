<style>
.preview {
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 4px;
    border: 1px solid rgba(0,0,0,.2);
    margin: 8px 0;
    width: 300px;
    height: 300px;
}
</style>

<BootstrapLayout onLoaded={onLoaded}>
    <form id="demoForm" method="POST">
        <div class="form-group row">
            <label class="col-sm-3 col-form-label">Avatar</label>
            <div class="col-sm-5">
                <input type="file" class="form-control" name="avatar" />
                <div id="avatarPreview" class="preview"></div>
            </div>
        </div>
    </form>
</BootstrapLayout>

<script>
import { onDestroy } from 'svelte';

import formValidation from 'formvalidation/dist/es6/core/Core';
import DemoFrame from 'formvalidation/dist/es6/plugins/DemoFrame';
import Icon from 'formvalidation/dist/es6/plugins/Icon';
import Trigger from 'formvalidation/dist/es6/plugins/Trigger';
import Bootstrap from 'formvalidation/dist/es6/plugins/Bootstrap';

import sampleCode from './bootstrap.programmatic';
import BootstrapLayout from '../../../../../components/demo/BootstrapLayout.svelte';

let fv;

const onLoaded = () => {
    fv = formValidation(document.getElementById('demoForm'), {
        fields: {
            avatar: {
                validators: {
                    notEmpty: {
                        message: 'The avatar is required'
                    },
                    promise: {
                        promise: function (input) {
                            return new Promise((resolve, reject) => {
                                const files = input.element.files
                                if (!files.length || typeof FileReader === 'undefined') {
                                    resolve({
                                        valid: true
                                    });
                                }

                                const img = new Image();
                                img.addEventListener('load', function() {
                                    const w = this.width;
                                    const h = this.height;

                                    resolve({
                                        valid: (w <= 300 && h <= 300),
                                        message: 'The avatar width and height must be less than 300 px',
                                        meta: {
                                            source: img.src,    // We will use it later to show the preview
                                            width: w,
                                            height: h,
                                        },
                                    });
                                });
                                img.addEventListener('error', function() {
                                    reject({
                                        valid: false,
                                        message: 'Please choose an image',
                                    });
                                });

                                const reader = new FileReader();
                                reader.readAsDataURL(files[0]);
                                reader.addEventListener('loadend', function(e) {
                                    img.src = e.target.result;
                                });
                            });
                        }
                    },
                }
            },
        },
        plugins: {
            trigger: new Trigger(),
            bootstrap: new Bootstrap(),
            icon: new Icon({
                valid: 'fa fa-check',
                invalid: 'fa fa-times',
                validating: 'fa fa-refresh'
            }),
            demoFrame: new DemoFrame({
                sender: '/guide/validators/promise/basic/bootstrap',
                sampleCode: sampleCode,
            }),
        },
    }).on('core.validator.validated', (e) => {
        if (e.field === 'avatar' && e.validator === 'promise') {
            const preview = document.getElementById('avatarPreview');
            if (e.result.valid && e.result.meta && e.result.meta.source) {
                // Preview the avatar
                const img = document.createElement('img');
                img.setAttribute('src', e.result.meta.source);
                img.setAttribute('style', 'max-width: 100%; height: auto;');

                preview.innerHTML = '';
                preview.appendChild(img);
            } else if (!e.result.valid) {
                preview.innerHTML = 'Preview';
            }
        }
    });
};

onDestroy(() => {
    fv && fv.destroy();
});
</script>
