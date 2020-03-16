<!--
  - Copyright 2020 LABOR.digital
  -
  - Licensed under the Apache License, Version 2.0 (the "License");
  - you may not use this file except in compliance with the License.
  - You may obtain a copy of the License at
  -
  -     http://www.apache.org/licenses/LICENSE-2.0
  -
  - Unless required by applicable law or agreed to in writing, software
  - distributed under the License is distributed on an "AS IS" BASIS,
  - WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  - See the License for the specific language governing permissions and
  - limitations under the License.
  -
  - Last modified: 2020.03.15 at 17:39
  -->

<template>
	<div class="preview">
		<div class="preview__iframeContainer" :class="{'preview__iframeContainer--blockInput': blockInput}"
			 :style="{'height': height + 'px'}">
			<vue-draggable-resizable class="resizable" :parent="true" :w="width" :h="height"
									 :draggable="false" :handles="['mr']" :minWidth="270" :active="true"
									 :prevent-deactivation="true" :onResizeStart="onResizeStart"
									 @resizestop="onResizeEnd">
				<iframe :src="href" :style="{'height': height + 'px'}"></iframe>
			</vue-draggable-resizable>
		</div>
		<a :href="href" class="preview__link" target="_blank">Open the example in a new tab</a>
	</div>
</template>

<script lang="ts">
	export default {
		name: "Preview",
		props: {
			href: String,
			height: {
				type: Number,
				default: 180
			}
		},
		data() {
			return {
				width: 250,
				blockInput: false
			}
		},
		methods: {
			onResizeStart(){
				this.blockInput = true;
			},
			onResizeEnd(){
				this.blockInput = false;
			}
		},
		mounted() {
			this.width = this.$el.clientWidth;
		}
	};
</script>

<style>
	.resizable{
		border: 1px solid #cfd4db;
		border-radius: 5px;
		width: 100%;
	}
	
	.preview {
		margin-top: 15px;
	}
	
	.preview,
	.preview__iframeContainer{
		position: relative;
		width: 100%;
	}
	
	.preview__iframeContainer--blockInput {
		pointer-events: none;
	}
	
	.preview__link {
		display: block;
		margin: 15px 0
	}
	
	iframe {
		width: 100%;
		height: 100%;
		border: none;
	}
	
	.handle.handle-mr {
		pointer-events: all;
		right: -20px;
		width: 15px;
		height: 15px;
		background-color: #3eaf7c;
		border: none;
		border-radius: 5px;
	}
	
	.handle.handle-mr:after {
		position: relative;
		display: block;
		content: "<>";
		color: #fff;
		font-size: 10px;
		line-height: 15px;
		width: 100%;
		text-align: center;
	}

</style>