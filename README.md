# testrepo
<?php
//template Name:web app

get_header(); ?> 

 <!-- banner_section -->
<section class="design_bnr overlay_1" style="background-image: url(<?php echo wp_get_attachment_url( get_post_thumbnail_id($post->ID) ); ?>);">
    <div class="container">
        <div class="banner_inr wow fadeInUp">
           <div class="buis_cnt">
                <?php while (have_posts()) : the_post(); ?>
                    <?php the_content(); ?>
                <?php endwhile; ?>
            </div>
            <div class="explore_sol text-center">
                <ul>
                    <li>
                        <a href="<?php the_field('banner_button_link'); ?>" class="exp_btn goto_section">
                            <?php the_field('wb_button_txt'); ?>
                        </a>
                    </li>
                    <li>
                        <a href="<?php the_field('own_web_link'); ?>" class="build_btn goto_section">
                            <?php the_field('own_web_text'); ?>
                        </a>
                    </li>
                </ul>
            
            </div>
        </div>
    </div>
</section>

<!-- banner_section ends -->

<!-- target_section -->

<section class="target_section">
    <div class="target_inr trgt_inr_new">
        <div class="container">
            <?php while(the_repeater_field('wb_app_targets')): ?>
                <div class="target_item wow zoomIn">
                    <span>
                        <img src="<?php the_sub_field('wb_target_icon'); ?>" alt=""/>
                    </span>
                    <h3><?php the_sub_field('target_nmbr'); ?></h3>
                    <p><?php the_sub_field('target_nme'); ?></p>
                </div>
            <?php endwhile; ?>
        </div>
    </div>
</section>

<!-- target_section ends -->

<!-- product_stories -->
<section class="product_stories">
    <div class="container">
        <div class="stories_inr">
            <div class="design_story_top web_story_top wow flipInX">
                <h2><?php the_field('visitor_heading'); ?></h2>
                <?php the_field('visitor_description'); ?>
            </div>

             <div class="process_cnt">
                <div class="procss_outer">
                    <div class="process_bar">
                        <div class="process_line">
                        </div>
                    </div>
                </div>
                <div class="process_action">
                    <?php
                    $trgtt=1;
                     while(the_repeater_field('wb_process')): if($trgtt == 1):?>  
                    <button class="process_item active_tab">   
                        <div class="process_no">
                            0<?php echo $trgtt; ?>
                        </div>
                        <div class="process_icon">
                            <div class="process_ring1"></div>
                            <div class="process_ring2"></div>
                            <div class="process_ring3"></div>
                            <div class="process_ring4"></div>
                            <div class="process_ring5"></div>
                            <div class="process_ring6"></div>
                        </div>
                        <div class="process_title">
                            <?php the_sub_field('process_heading'); ?>
                        </div>
                        <div class="process_text">
                            <?php the_sub_field('process_description',false,false); ?>  
                        </div>
                    </button>
                    <?php else: ?>
                    <button class="process_item">   
                        <div class="process_no">
                            0<?php echo $trgtt; ?>
                        </div>
                        <div class="process_icon">
                            <div class="process_ring1"></div>
                            <div class="process_ring2"></div>
                            <div class="process_ring3"></div>
                            <div class="process_ring4"></div>
                            <div class="process_ring5"></div>
                            <div class="process_ring6"></div>
                        </div>
                        <div class="process_title">
                            <?php the_sub_field('process_heading'); ?>
                        </div>
                        <div class="process_text">
                            <?php the_sub_field('process_description',false,false); ?>  
                        </div>
                    </button>
                    <?php endif; $trgtt++; endwhile; ?>
                </div>
             </div>
            
            <div class="explore_sol text-right">
                <a href="#ftr_frm" class="exp_btn goto_section">
                    Get started
                </a>
             </div>
        </div>
    </div>
</section>
<!-- product_stories ends -->


<!-- process_section -->

<section class="process_section web_app_section" id="three_sec_two">
    <div class="container">             
        <div class="strategy_cnt_outer">
            <ul class="nav nav-tabs strategy_tabs" id="myTab" role="tablist">
                <?php $hdgn=1; $count=0; $hdgn_ary=array('home','profile','contact'); 
                while(the_repeater_field('web_app_headings')):  ?>
                  <li class="nav-item">
                    <a class="nav-link <?php if($hdgn==1){ echo 'active'; } ?>" id="<?php echo $hdgn_ary[$count]; ?>-tab" data-toggle="tab" href="#<?php echo $hdgn_ary[$count]; ?>" role="tab" aria-controls="<?php echo $hdgn_ary[$count]; ?>" aria-selected="<?php if($hdgn==1){ echo 'true'; } else { echo 'false'; } ?>"><?php echo $hdgn; ?>. <?php the_sub_field('wb_ap_heading'); ?></a>
                  </li>
                <?php $hdgn++; $count++; endwhile; ?>
            </ul>
            <div class="tab-content" id="myTabContent">
                <?php $clb_ary=array('home','profile','contact');
                $clb_cnt=0;
                while(the_repeater_field('collaborations')): ?>
              <div`  class="tab-pane fade <?php if($clb_cnt==0){ echo 'show active'; } ?>" id="<?php echo $clb_ary[$clb_cnt]; ?>" role="tabpanel" aria-labelledby="<?php echo $clb_ary[$clb_cnt]; ?>-tab">
                    <div class="strategy_cnt">
                        <div class="row">
                            <div class="col-lg-5 col-md-5 wow fadeInLeft">
                                <div class="cncpt_thumb">
                                    <img src="<?php the_sub_field('clb_image'); ?>" alt=""/>
                                </div>
                            </div>
                            <div class="col-lg-7 col-md-7 wow fadeInRight">
                                <div class="cncpt_cnt">
                                    <div class="cncpt_hdr">
                                        <h3><?php the_sub_field('clb_heading'); ?></h3>
                                    </div>
                                    <div class="cncpt_txt">
                                        <?php the_sub_field('clb_description'); ?>
                                    </div>
                                    <div class="process_points web_app_points wb_pnts">
                                        <ul>
                                            <?php $inr_cnt=1; while(the_repeater_field('clb_points')): ?>
                                                <li><?php the_sub_field('clb_pnt'); ?></li>
                                                <?php if($inr_cnt%3==0){
                                                    echo '</ul><ul>';
                                                    } ?>
                                            <?php $inr_cnt++; endwhile; ?>
                                        </ul>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div class="explore_sol text-center">
                            <a href="<?php the_sub_field('clb_button_link'); ?>" class="exp_btn goto_section">
                                <?php the_sub_field('clb_button_text'); ?>
                            </a>
                        </div>
                   </div>
              </div>
              <?php $clb_cnt++; endwhile; ?>
            </div>
        </div>
    </div>
</section>

<!-- process_section ends -->


<!-- creativity section -->

<section class="creativity_section elixir_section">
    <div class="container">
        <div class="creativity_cnt">
         <div class="creative_txt">
             <h3><?php the_field('elixir_section_heading'); ?></h3>
          </div>
         <div class="row">
            <div class="col-lg-4 order-sm-2 col-md-5 wow fadeInRight">
                <div class="creative_thumb">
                    <img src="<?php the_field('elixir_section_image'); ?>" alt=""/>
                </div>
            </div>
            <div class="col-lg-8 col-md-7 wow fadeInLeft">
                 <div class="creative_txt elixir_txt">
                    <div class="design_struct_outer">
                        <div class="design_struct">
                           <h4><?php the_field('elixir_section_subheading'); ?></h4>
                           <?php the_field('elixir_section_description'); ?>
                    
                        </div>
                    </div>
                 </div>
            </div>
        </div>
        <div class="explore_sol text-center">
            <a href="<?php the_field('elixir_section_button_link'); ?>" class="exp_btn goto_section">
                <?php the_field('elixir_section_button_text'); ?>
            </a>
        </div>
    </div>
    </div>
</section>

<!-- creativity section ends -->

<!-- Opportunities_section -->
<section class="Opport_section customer_fav graphics_section">
    <div class="container">
        <div class="creative_txt wd60">
            <h3><?php the_field('infographics_heading'); ?> </h3>
         </div>
            <div class="stories_section">
                <div class="row new_desktop">
                	<?php 
                	$tm=.1;
			            $argall =array('post_type'  => 'post', 'order' => 'ASC','posts_per_page' =>-1, 'cat'=> 22); 
						$totalpage=query_posts($argall);  
						$args = array('post_type'  => 'post', 'posts_per_page' => 12,'order' => 'ASC', 'cat'=> 22); 
           				query_posts($args);
						while ( have_posts() ) : the_post(); ?>
                  
                    <div class="col-lg-3 col-md-4 col-sm-6 wow fadeInUp" data-wow-delay="<?php echo $tm; ?>s">
                        <div class="stories_thumb">
                        	<a href="<?php echo get_the_permalink(); ?>"><img src="<?php the_field('thumbnail_image'); ?>" alt=""/>
                            </a>
                        </div>
                        <div class="stories_cnt">
                            <h4><?php the_time('F j, Y'); ?></h4>
                            <p><?php the_title(); ?></p>
                            <a href="<?php echo get_the_permalink(); ?>">
                                lees meer
                            </a>
                        </div>
                    </div>
                    <?php $tm=$tm+.1; ?><input type="hidden" value="1" class="pg">
										<?php endwhile; ?>
										<?php wp_reset_query(); ?>
                </div>
                <div align="center">
								    	<img id="load_img" style="display: none" src="<?php echo get_template_directory_uri(); ?>/assets/images/loader.gif"  alt="" />
								    </div>
                  <div class="explore_sol text-center">
                  
                <a href="javascript:void(0)" class="exp_btn goto_section" id="loadmore-sec">
                    <?php the_field('infographics_button_text'); ?><!-- View all work -->
                </a>
                <!-- <div class="conct_btn"></div> -->
            </div>
            </div>

          
        </div>
</section>

<!-- Opportunities_section ends -->

<!-- service model -->
<section class="service_model">
    <div class="container ">
        <div class="mob_inr clearfix">
            <div class="mob_thumb wow fadeInRight">
                <img src="<?php the_field('ruby_section_image'); ?>" alt=""/>
            </div>
            <div class="model_cnt mob_cnt wow fadeInLeft">
                <div class="creative_txt">
                    <h3><?php the_field('ruby_section_heading'); ?></h3>
                </div>
                <?php the_field('ruby_section_description'); ?>
                <div class="mob_points">
                    <ul>
                        <?php while(the_repeater_field('ruby_section_points')): ?>
                            <li><?php the_sub_field('ruby_point'); ?></li>
                        <?php endwhile; ?>
                    </ul>
                </div> 
            </div>
        </div>
    </div>
</section>

<!-- service model ends -->

<!-- customize_section -->

<section class="customize_section native_section" style="background-image: url(<?php the_field('work_section_background_image'); ?>)";>
    <div class="container">
        <div class="custom_outer">
            <div class="customize_cnt wd60 wow flipInX">
                 <div class="creative_txt">
                    <h3><?php the_field('work_heading'); ?></h3>
                     <p><?php the_field('works_description'); ?></p>
                </div>
            </div>
            <div class="wordpress_design wow fadeIn">
                <img src="<?php the_field('work_section_image'); ?>" alt=""/>
            </div>
        </div>
    </div>
</section>

<!-- customize_section ends -->

<!-- requirement_section -->
<section class="requirement_section">
    <div class="container">
        <div class="require_inr">
            <div class="row">
                <?php $tm=.2; while(the_repeater_field('requirements')): ?>
                    <div class="col-lg-4 col-md-4 col-sm-6 wow fadeInUp" data-wow-delay="<?php echo $tm; ?>s">
                        <div class="require_item">
                            <div class="require_thumb">
                                <img src="<?php the_sub_field('requirement_icon'); ?>" alt=""/>
                            </div>
                            <div class="require_cnt">
                                <h4><?php the_sub_field('requirement_heading'); ?></h4>
                                <p><?php the_sub_field('requirement_description'); ?></p>
                            </div>
                        </div>
                    </div>
                <?php $tm=$tm+.2; endwhile; ?>
            </div>
        </div>
        <div class="hire_section">
            <div class="hire_hdr">
                <h2><?php the_field('professional_developer_heading'); ?></h2>
            </div>
            <div class="hire_inr clearfix">
                <div class="hire_lft">
                    <div class="hire_cnt">
                        <?php the_field('professional_developer_description'); ?>
                    </div>
                    <div class="learn_sec">
                        <a href="<?php the_field('learn_more_link'); ?>" class="lrn_btn goto_section">
                            Learn more
                            <span><i class="fas fa-arrow-right"></i></span>
                        </a>
                    </div>
                </div>
                <div class="designer_slider">
                    <div class="customerSlider">
                        <?php $k=1; while(the_repeater_field('professional_developer_images')): ?>    
                            <div class="customerSliderItem <?php if($k==1){ echo 'active'; } ?>">
                                <a href="javascript:void(0)" class="customerImg">
                                    <img src="<?php the_sub_field('developer_img'); ?>" alt="" />
                                </a>
                                <div class="wishCell">
                                    <i class="fas fa-heart"></i>
                                </div>
                            </div>
                        <?php $k++; endwhile; ?>
                    </div>
                </div>
            </div>
            <div class="explore_sol text-center">
            	
                <a href="<?php the_field('professional_developer_button_link'); ?>" class="exp_btn goto_section">
                    Hire Dedicated Designer<!-- View all work -->
                </a>
            </div>
        </div>
    </div>
</section>
<!-- requirement_section ends -->

<!-- finalize section -->

<section class="creativity_section redesign_section">
    <div class="container">
        <div class="creativity_cnt">
            <div class="row">
                <div class="col-lg-5 wow fadeInLeft">
                    <div class="creative_thumb">
                        <img src="<?php the_field('redesign_section_image'); ?>" alt=""/>
                    </div>
                </div>
                <div class="col-lg-7 wow fadeInRight">
                     <div class="creative_txt">
                        <h3><?php the_field('redesign_section_heading'); ?></h3>
                        <p><?php the_field('redesign_section_subheading'); ?></p>
                        <ul>
                            <?php while(the_repeater_field('redesign_section_points')): ?>
                                <li class="clearfix">
                                    <span>
                                        <svg><use xmlns:xlink="http://www.w3.org/1999/xlink" xlink:href="#ckck_icon"></use></svg>
                                    </span>
                                    <label><?php the_sub_field('redesign_point'); ?></label>
                                </li>
                            <?php endwhile; ?>
                        </ul>
                        <div class="explore_sol">
                            <a href="<?php the_field('redesign_button_link'); ?>" class="exp_btn goto_section">
                                <?php the_field('redesign_button_text'); ?>
                            </a>
                        </div>
                     </div>
                </div>
            </div>
        </div>
    </div>
</section>

<!-- finalize section ends -->


<!-- award_section -->
<section class="award_section">
    <div class="container">
        <div class="award_inr">
            <div class="award_thumb">
                <img src="<?php the_field('award_section_dove_image',7); ?>" alt=""/>
            </div>
            <div class="steps_cnt">
                <?php the_field('award_section_content',7); ?>
               <!--  <h2>Collaborate with award-winning hands to help your charity or non-profit.</h2>
                <p>we’re honored to help passionate organizations like these make a positive impact on the world.We believe that top talent in design and development shouldn’t benefit only those that can afford it.</p> -->
            </div> 
            <div class="think_blk wow fadeInUp">
                <span>
                    <img src="<?php the_field('award_section_think_image',7); ?>" alt=""/>
                </span>
                <h4><?php the_field('text_under_think_image',7); ?></h4>
                <div class="explore_sol text-center">
                <a href="<?php the_field('award_section_button_link',7); ?>" class="exp_btn goto_section">
                    <?php the_field('award_section_button_text',7); ?>
                </a>
            </div>
            </div> 
        </div>
    </div>
</section>
<!-- award_section ends -->


<?php get_footer(); ?>
<script>
		  jQuery(document).ready(function($){
		$("#loadmore-sec").click(function(){
		  	var x=$('.pg:last').val();
		  		$('#load_img').show();
			var data= { action: 'desktop_load_more', 'lastpg' :x };
			
		   	jQuery.post(ajaxurl, data,function(response) {
		   	$('#load_img').hide();
		$('.new_desktop').append(response);
		
		setTimeout(function(){ 
		var y=Math.ceil((<?php echo count($totalpage); ?>)/12);
		if(	$('.pg:last').val()==y)
		{
		$('#loadmore-sec').hide();
		}
		 }, 400);
		});
		});
		});
</script>
