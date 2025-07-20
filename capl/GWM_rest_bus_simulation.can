/*@!Encoding:1252*/
includes
{
  
}

variables
{
  message Ball_Game_Mode_CAN CAN_BALL_GAME_MODE_CAN;//fixed_periodic
  message ABS_Msg_Data_CAN CAN_ABS_MSG_DATA_CAN;//event_periodic
  message RDS_Coder_Data_CAN CAN_RDS_CODER_DATA_CAN;//event_message
  
  msTimer timer_Ball_Game_Mode_CAN;//fixed_periodic
  msTimer timer_ABS_Msg_Data_CAN;//event_periodic
  
  
  const long Timer_value_Ball_Game_Mode_CAN=50;//fixed_periodic
  const long Timer_value_ABS_Msg_Data_CAN=1500;//event_periodic
  
}
on start
{
 setTimer(timer_Ball_Game_Mode_CAN,Timer_value_Ball_Game_Mode_CAN);//fixed_periodic
 setTimer(timer_ABS_Msg_Data_CAN,Timer_value_ABS_Msg_Data_CAN);//event_periodic
}
// start code of ball_game_mode_fixed_periodic
on timer timer_Ball_Game_Mode_CAN
{
  sendBall_Game_Mode_CAN ();
  setTimer(timer_Ball_Game_Mode_CAN,Timer_value_Ball_Game_Mode_CAN);
} 
void sendBall_Game_Mode_CAN ()
{
 byte main_switch_value;
 byte miss_switch_value;
 main_switch_value= @main_panel::sys_main_switch;
 miss_switch_value= @main_panel::sys_miss_switch_ball_game_mode;
 if(main_switch_value==0 && miss_switch_value==0)
  { 
    output(CAN_BALL_GAME_MODE_CAN);
  }
}

   on sysvar GSW_Ball::sys_Actv_Live_1_Rq
    {
    CAN_BALL_GAME_MODE_CAN.Actv_Live_1_Rq= @GSW_Ball::sys_Actv_Live_1_Rq;
    }
   on sysvar GSW_Ball::sys_Actv_Live_2_Rq
    {
    CAN_BALL_GAME_MODE_CAN.Actv_Live_2_Rq= @GSW_Ball::sys_Actv_Live_2_Rq;
    }
 on sysvar GSW_Ball::sys_Preset_6_Bank_Rq
  {
    if(@GSW_Ball::sys_Preset_6_Bank_Rq <= 0x7)
    {
      CAN_BALL_GAME_MODE_CAN.Preset_6_Bank_Rq= @GSW_Ball::sys_Preset_6_Bank_Rq;
    }
    else
    {
      openPanel("ERRORPANEL");
    }
  }
  on sysvar GSW_Ball::sys_Preset_12_Bank_Rq
  {
    if(@GSW_Ball::sys_Preset_12_Bank_Rq <= 0xF)
    {
      CAN_BALL_GAME_MODE_CAN.Preset_12_Bank_Rq = @GSW_Ball::sys_Preset_12_Bank_Rq;
    }
    else
    {
      openPanel("ERRORPANEL");
    }
  }
  on sysvar GSW_Ball::sys_FM_Menu_Data_Rq
  {
    if(@GSW_Ball::sys_FM_Menu_Data_Rq <= 0xFF)
    {
      CAN_BALL_GAME_MODE_CAN.FM_Menu_Data_Rq = @GSW_Ball::sys_FM_Menu_Data_Rq;
    }
    else
       {
      openPanel("ERRORPANEL");
    }
  }
  on sysvar GSW_Ball::sys_AM_Menu_Data_Rq
  {
    if ( @GSW_Ball::sys_AM_Menu_Data_Rq <= 0xFFFF)
    {
      CAN_BALL_GAME_MODE_CAN.AM_Menu_Data_Rq= @GSW_Ball::sys_AM_Menu_Data_Rq;
    }
    else
       {
      openPanel("ERRORPANEL");
    }}
     
      on sysvar main_panel::sys_miss_switch_ball_game_mode
      {
        if ( @main_panel::sys_miss_switch_ball_game_mode == 0x1)
          {
          cancelTimer( timer_Ball_Game_Mode_CAN);
        }
        else
        {
setTimer(timer_Ball_Game_Mode_CAN,Timer_value_Ball_Game_Mode_CAN);
        }
      }
      // end_of_ball_game_mode_code_fixed_periodic
      
  on sysvar main_panel::sys_main_switch
      {
        if ( @main_panel::sys_main_switch== 0x1)
        {
          cancelTimer( timer_Ball_Game_Mode_CAN);//fixed_periodic
          cancelTimer (timer_ABS_Msg_Data_CAN);//event_periodic
        }
        else
        {
          setTimer(timer_Ball_Game_Mode_CAN,Timer_value_Ball_Game_Mode_CAN);//fixed_periodic
          setTimer(timer_ABS_Msg_Data_CAN,Timer_value_ABS_Msg_Data_CAN);//event_periodic
        }
      }
      
      
  // start code of ABS_Msg_Data_CAN_event_periodic
      
  on timer timer_ABS_Msg_Data_CAN
   {
     sendABS_Msg_Data_CAN();
    setTimer(timer_ABS_Msg_Data_CAN,Timer_value_ABS_Msg_Data_CAN);
  }
  void sendABS_Msg_Data_CAN()
  {
    if(@main_panel::sys_main_switch==0 && @main_panel::sys_miss_switch_ABS_Msg_Data_CAN==0)
    {
      output(CAN_ABS_MSG_DATA_CAN);
    }
  }
  
 on sysvar GWS_ABS::sys_HMI_MID_Sgnl_1_Rq
  {
    if(@GWS_ABS::sys_HMI_MID_Sgnl_1_Rq<= 0xF)
    {
      CAN_ABS_MSG_DATA_CAN.HMI_MID_Sgnl_1_Rq= @GWS_ABS::sys_HMI_MID_Sgnl_1_Rq;
      sendABS_Msg_Data_CAN();
    }
    else
    {
      openpanel("ERRORPANEL");
    }
  }
  
 on sysvar GWS_ABS::sys_HMI_MID_Sgnl_2_Rq
  {
    if(@GWS_ABS::sys_HMI_MID_Sgnl_2_Rq<= 0xF)
    {
      CAN_ABS_MSG_DATA_CAN.HMI_MID_Sgnl_2_Rq= @GWS_ABS::sys_HMI_MID_Sgnl_2_Rq;
      sendABS_Msg_Data_CAN();
    }
    else
    {
      openpanel("ERRORPANEL");
    }
  }     
  on sysvar GWS_ABS::sys_HMI_MID_Sgnl_3_Rq
  {
    if(@GWS_ABS::sys_HMI_MID_Sgnl_3_Rq<= 0xF)
    {
      CAN_ABS_MSG_DATA_CAN.HMI_MID_Sgnl_3_Rq= @GWS_ABS::sys_HMI_MID_Sgnl_3_Rq;
      sendABS_Msg_Data_CAN();
    }
    else
    {
      openpanel("ERRORPANEL");
    }
  }          
  
 on sysvar GWS_ABS::sys_MID_Data_Rq
  {
    if (@GWS_ABS::sys_MID_Data_Rq <= 255)
    {
    CAN_ABS_MSG_DATA_CAN.MID_Data_Rq = @GWS_ABS::sys_MID_Data_Rq;
    sendABS_Msg_Data_CAN();
    }
    else
    {
      openpanel("ERRORPANEL");
    }
  }    
 on sysvar GWS_ABS::sys_MID_Msg_Rq
  {
    CAN_ABS_MSG_DATA_CAN.MID_Msg_Rq = @GWS_ABS::sys_MID_Msg_Rq;
    sendABS_Msg_Data_CAN();
  }
 on sysvar GWS_ABS::sys_Indictr_Lft_Dsply
  {
    CAN_ABS_MSG_DATA_CAN.Indictr_Lft_Dsply = @GWS_ABS::sys_Indictr_Lft_Dsply;
    sendABS_Msg_Data_CAN();
  }
  on sysvar GWS_ABS::sys_Indictr_Rgt_Dsply
  {
   CAN_ABS_MSG_DATA_CAN.Indictr_Rgt_Dsply = @GWS_ABS::sys_Indictr_Rgt_Dsply;
    sendABS_Msg_Data_CAN();
  }
  on sysvar main_panel::sys_miss_switch_ABS_Msg_Data_CAN
  {
    if(@main_panel::sys_miss_switch_ABS_Msg_Data_CAN == 0x1)
    {
      cancelTimer(timer_ABS_Msg_Data_CAN);
    }
    else
    {
      setTimer(timer_ABS_Msg_Data_CAN,Timer_value_ABS_Msg_Data_CAN);
    }
  }
   // end_of_ABS_Msg_Data_CAN_event_periodic
  
  //start_of_RDS_Coder_Data_CAN_event_message
  
 void sendRDS_Coder_Data_CAN()
  {
    if(@main_panel::sys_main_switch== 0x0)
    {
      output(CAN_RDS_CODER_DATA_CAN);
    }
  }
  on sysvar GSW_RDS::sys_TA_Data_Rq
  {
    CAN_RDS_CODER_DATA_CAN.TA_Data_Rq = @GSW_RDS::sys_TA_Data_Rq;
    sendRDS_Coder_Data_CAN();
  }
  on sysvar GSW_RDS::sys_TP_Data_Rq
  {  if( @GSW_RDS::sys_TP_Data_Rq <= 0xF)
    {
      CAN_RDS_CODER_DATA_CAN.TP_Data_Rq = @GSW_RDS::sys_TP_Data_Rq;
      sendRDS_Coder_Data_CAN();
    }
    else{
      openPanel ("ERRORPANEL");
    }
    }
  on sysvar GSW_RDS::sys_Sig_Spdmtr_Rq
  {
     if( @GSW_RDS::sys_Sig_Spdmtr_Rq <= 240)
    {
      CAN_RDS_CODER_DATA_CAN.Sig_Spdmtr_Rq = @GSW_RDS::sys_Sig_Spdmtr_Rq;
      sendRDS_Coder_Data_CAN();
    }
    else{
      openPanel ("ERRORPANEL");
    }
    }
   on sysvar GSW_RDS::sys_Ahb_Dsply
  {CAN_RDS_CODER_DATA_CAN.Ahb_Dsply= @GSW_RDS::sys_Ahb_Dsply;
    sendRDS_Coder_Data_CAN();
  }
    